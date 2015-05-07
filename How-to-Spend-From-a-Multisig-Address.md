This example is a continuation of [How to Create a Multisig Address](How-to-Create-a-Multisig-Address).

Send 0.001 bitcoins (100000 satoshis) to the multisig address `3A6oGpJ5MzABAj9PofXKjcpTJCgYrdGBNJ` using any Bitcoin wallet.

View the [example transaction](https://blockchain.info/tx/f759759bc998ec96879e4ae8c1639e8a186e0d507401eb32e4479de64d340605) on blockchain.info.

### Confirm Receipt of Bitcoin
Look up the **balance** of the multisig address.
```sh
$ bx fetch-balance 3A6oGpJ5MzABAj9PofXKjcpTJCgYrdGBNJ
```
```js
balance
{
    address 3A6oGpJ5MzABAj9PofXKjcpTJCgYrdGBNJ
    confirmed 100000
    received 100000
    unspent 100000
}
```
Notice that `balance.confirmed` shows that the transaction has at least one confirmation.
### Create a Transaction
Look up the preceding **transaction** by its hash.
```sh
$ bx fetch-tx f759759bc998ec96879e4ae8c1639e8a186e0d507401eb32e4479de64d340605
```
```js
transaction
{
    hash f759759bc998ec96879e4ae8c1639e8a186e0d507401eb32e4479de64d340605
    inputs
    {
        input
        {
            address 1FLrh6Q1URcdSNKYCSnQwdpakpPPmwg7xd
            previous_output
            {
                hash 6098bb548c49dd9934650627f07f3bd62bf8f3cb4aab391edc0ea36fe82b1081
                index 0
            }
            script "[ 3045022100cf822811fb316a42844f8b30a5e1026ec8ab7df58e1b28a1a8cf2d6522f9390302204549cdcb6956bdfbea59698aea443281a208972fa02a6cb3f796aaa3191bff9601 ] [ 04f539b68ab0d5c0c75a78e81a86d76aafd83fa7978d55f347fb583a461af37b72babce7680b67e5760e6af74024e2526d8670d94158697b72f665a770f8fa58fe ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1KDCjpWXE2VbFotygTQ4T3jThz65YmfEq6
            script "dup hash160 [ c7c10de3b95e020766d0c98d087a0cef2dfecbbe ] equalverify checksig"
            value 3999880000
        }
        output
        {
            address 3A6oGpJ5MzABAj9PofXKjcpTJCgYrdGBNJ
            script "hash160 [ 5c406de4915e37a7e71c7ef9bff42fbf1404daa0 ] equal"
            value 100000
        }
    }
    version 1
}
```
The **input** for the new transaction will be `transaction.outputs[1]` (because it is the unspent output of the multisig address). This input is formatted as `transaction hash:index`, where the index is the zero-based position of this previous output in its transaction.
```
f759759bc998ec96879e4ae8c1639e8a186e0d507401eb32e4479de64d340605:1
```
The **output** for the new transaction is formatted as `address:amount`, where the amount is a number of satoshis. There are 100,000 satoshis available to spend, of which this transaction will spend 55% to [Freenet](https://blockchain.info/address/1966U1pjj15tLxPXZ19U48c99EJDkdXeqb).
```
1966U1pjj15tLxPXZ19U48c99EJDkdXeqb:55000
```
In this example the remainder will not be spent to any address. This will result in 45,000 satoshis being earned by miners as a transaction fee.

Construct the **transaction** from the inputs and outputs, in this case one of each.
```sh
$ bx tx-encode -i f759759bc998ec96879e4ae8c1639e8a186e0d507401eb32e4479de64d340605:1 -o 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb:45000
```
```
01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f70100000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
Inspect the transaction visually.
```sh
$ bx tx-decode 01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f70100000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```js
transaction
{
    hash 028678bd699174ca9c305b81fe78d69c28cb2483ead9f492cd25bfac787326a4
    inputs
    {
        input
        {
            previous_output
            {
                hash f759759bc998ec96879e4ae8c1639e8a186e0d507401eb32e4479de64d340605
                index 1
            }
            script ""
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb
            script "dup hash160 [ 58b7a60f11a904feef35a639b6048de8dd4d9f1c ] equalverify checksig"
            value 45000
        }
    }
    version 1
}
```
Notice that `transactions.inputs[0].script` is empty. This means that the input has not been endorsed.

Create the first **endorsement** for the first input `028678bd...:0` of the new transaction, using the first private key, the multisig script and the new transaction.
```sh
$ bx input-sign 9d695afea1c3ab99e11248e4b74e698332b11f5c5c051e6e80da61aa19ae7c89 "2 [ 02b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b ] [ 025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c ] [ 021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f010 ] 3 checkmultisig" 01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f70100000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
30440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b901
```
Create the second **endorsement** for the first input `028678bd...:0` of the new transaction, using the second private key, the multisig script and the new transaction.
```sh
$ bx input-sign 68ebab45a918444d7e088c49bda76d7df89b9ea6ba5ddeb1aab5945391828b83 "2 [ 02b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b ] [ 025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c ] [ 021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f010 ] 3 checkmultisig" 01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f70100000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
3045022100aa9096ce71995c24545694f20ab0482099a98c99b799c706c333c521e51db66002206578f023fa46f4a863a6fa7f18b95eebd1a91fcdf6ce714e8795d902bd6b682b01
```
Encode the multisig script.
```sh
$ bx script-encode "2 [ 02b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b ] [ 025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c ] [ 021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f010 ] 3 checkmultisig"
```
```
522102b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b21025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c21021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f01053ae
```
Create an **endorsement script** using the two endorsements and the encoded multisig script, and assign it to the first input of the transaction.

> The zero opcode is necessary due to an [off-by-one error in the reference client](https://bitcoin.org/en/developer-guide#multisig).

```js
$ bx input-set "zero [ 30440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b901 ] [ 3045022100aa9096ce71995c24545694f20ab0482099a98c99b799c706c333c521e51db66002206578f023fa46f4a863a6fa7f18b95eebd1a91fcdf6ce714e8795d902bd6b682b01 ] [ 522102b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b21025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c21021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f01053ae ]" 01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f70100000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f701000000fdfd00004730440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b901483045022100aa9096ce71995c24545694f20ab0482099a98c99b799c706c333c521e51db66002206578f023fa46f4a863a6fa7f18b95eebd1a91fcdf6ce714e8795d902bd6b682b014c69522102b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b21025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c21021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f01053aeffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
### Validate and Broadcast the Transaction
Inspect the updated transaction visually.
```sh
$ bx tx-decode 01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f701000000fdfd00004730440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b901483045022100aa9096ce71995c24545694f20ab0482099a98c99b799c706c333c521e51db66002206578f023fa46f4a863a6fa7f18b95eebd1a91fcdf6ce714e8795d902bd6b682b014c69522102b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b21025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c21021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f01053aeffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```js
transaction
{
    hash 7aa068cab7f11aa25f34f32bd7b3480790af2facdf8192c59985e6282c336465
    inputs
    {
        input
        {
            address 3A6oGpJ5MzABAj9PofXKjcpTJCgYrdGBNJ
            previous_output
            {
                hash f759759bc998ec96879e4ae8c1639e8a186e0d507401eb32e4479de64d340605
                index 1
            }
            script "zero [ 30440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b901 ] [ 3045022100aa9096ce71995c24545694f20ab0482099a98c99b799c706c333c521e51db66002206578f023fa46f4a863a6fa7f18b95eebd1a91fcdf6ce714e8795d902bd6b682b01 ] [ 522102b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b21025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c21021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f01053ae ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb
            script "dup hash160 [ 58b7a60f11a904feef35a639b6048de8dd4d9f1c ] equalverify checksig"
            value 45000
        }
    }
    version 1
}
```
Notice that the endorsement script has been applied to `transaction.inputs[0].script` and that `transaction.hash` has been updated.

**Validate** the first endorsement of the transaction's first input, using the first public key, multisig script, first endorsement and transaction (optional).
```sh
$ bx input-validate 02b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b "2 [ 02b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b ] [ 025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c ] [ 021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f010 ] 3 checkmultisig" 30440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b901 01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f701000000fc004730440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b9014730440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b9014c69522102b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b21025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c21021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f01053aeffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
The endorsement is valid.
```
**Validate** the transaction against the blockchain (optional).
```sh
$ bx validate-tx 01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f701000000fdfd00004730440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b901483045022100aa9096ce71995c24545694f20ab0482099a98c99b799c706c333c521e51db66002206578f023fa46f4a863a6fa7f18b95eebd1a91fcdf6ce714e8795d902bd6b682b014c69522102b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b21025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c21021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f01053aeffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
The transaction is valid.
```
**Broadcast** the transaction to the blockchain.
```sh
$ bx send-tx 01000000010506344de69d47e432eb0174500d6e188a9e63c1e84a9e8796ec98c99b7559f701000000fdfd00004730440220695a28c42daa23c13e192e36a20d03a2a79994e0fe1c3c6b612d0ae23743064602200ca19003e7c1ce0cecb0bbfba9a825fc3b83cf54e4c3261cd15f080d24a8a5b901483045022100aa9096ce71995c24545694f20ab0482099a98c99b799c706c333c521e51db66002206578f023fa46f4a863a6fa7f18b95eebd1a91fcdf6ce714e8795d902bd6b682b014c69522102b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b21025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c21021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f01053aeffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
Sent transaction at 2015-May-06 23:24:55.
```
### Confirm Spend of Bitcoin
Look up the **balance** of the multisig address.
```sh
$ bx fetch-balance 3A6oGpJ5MzABAj9PofXKjcpTJCgYrdGBNJ
```
```js
balance
{
    address 3A6oGpJ5MzABAj9PofXKjcpTJCgYrdGBNJ
    confirmed 0
    received 100000
    unspent 0
}
```
View the [spend transaction](https://blockchain.info/tx/7aa068cab7f11aa25f34f32bd7b3480790af2facdf8192c59985e6282c336465) on blockchain.info.