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