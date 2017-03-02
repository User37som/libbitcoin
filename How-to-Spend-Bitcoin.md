This example is a continuation of [How to Receive Bitcoin](How-to-Receive-Bitcoin).
### Create a Transaction
Look up the preceding **transaction** by its hash.
```sh
$ bx fetch-tx 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
```
```js
transaction
{
    hash 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
    inputs
    {
        input
        {
            address 1PqLFcRyNMzsgcmT4Sd2XSVZ4XPb8CN8sj
            previous_output
            {
                hash df51c69f381a7511e95571382715cfd83c5384e9006ee7c546cfa6bb4b172346
                index 0
            }
            script "[304502206be979f1f89776e26abb40f458dc942d191d447cf3ce847d2d7e430df6b21ac4022100cade875670d71bd972f151b00544044d90a75261a9a01542968a1b36b31aea1801] [041fd7ca20852f638e82ac43b2df2ac7b38a3fec1622fb33c9f679ae909868a7e6e013429b2421a871a4e1d5d5702bea978bdd8ec399657dc6f3c0334a83de40bf]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
            script "dup hash160 [c564c740c6900b93afc9f1bdaef0a9d466adf6ee] equalverify checksig"
            value 100000
        }
        output
        {
            address 18kn866ztW2Y12DkijCubQmE6xBqmJS4Gr
            script "dup hash160 [55106ed6c650e125c28f767c83ccfbc0c231fc8a] equalverify checksig"
            value 328860000
        }
    }
    version 1
}
```
The **input** for the new transaction will be `transaction.outputs[0]`. This input is formatted as `transaction hash:index`, where the index is the zero-based position of this previous output in its transaction.
```
7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d:0
```
The **output** for the new transaction is formatted as `address:amount`, where the amount is a number of satoshis. There are 100,000 satoshis available to spend, of which this transaction will spend 45% to [Freenet](https://blockchain.info/address/1966U1pjj15tLxPXZ19U48c99EJDkdXeqb).
```
1966U1pjj15tLxPXZ19U48c99EJDkdXeqb:45000
```
In this example the remainder will not be spent to any address. This will result in 55,000 satoshis being earned by miners as a transaction fee.

Construct the **transaction** from the inputs and outputs, in this case one of each.
```sh
$ bx tx-encode -i 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d:0 -o 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb:45000
```
```
01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c0000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
Inspect the transaction visually.
```sh
$ bx tx-decode 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c0000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```js
transaction
{
    hash e433a95114dc4eb2209f7c329bad265890affb728a60ac1b967d99bbe1f25971
    inputs
    {
        input
        {
            previous_output
            {
                hash 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
                index 0
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
            script "dup hash160 [58b7a60f11a904feef35a639b6048de8dd4d9f1c] equalverify checksig"
            value 45000
        }
    }
    version 1
}
```
Notice that `transactions.inputs[0].script` is empty. This means that the input has not been endorsed.

Generate a random **nonce**.
```sh
$ bx seed
```
```
707e3d717925ba2e98234dd6f3a38eb5
```

> The above step is now **invalid** as a nonce is no longer allowed.

Create an **endorsement** for the first input `7c3e880e...:0` of the new transaction, using the private key, nonce, previous output script and the new transaction. The script is obtained from `transaction.outputs[0].script` in the input's transaction.
```sh
$ bx input-sign -n 707e3d717925ba2e98234dd6f3a38eb5 4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 "dup hash160 [c564c740c6900b93afc9f1bdaef0a9d466adf6ee] equalverify checksig" 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c0000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
30450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af6817401
```
Create an **endorsement script** using the endorsement and public key, and assign it to the first input of the transaction.
```js
$ bx input-set "[30450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af6817401] [03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31]" 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c0000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c000000006b4830450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af68174012103e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
### Validate and Broadcast the Transaction
Inspect the updated transaction visually.
```sh
$ bx tx-decode 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c000000006b4830450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af68174012103e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```js
transaction
{
    hash 37c9c4ee0e84c7c7924f74d92cf0779ec6e8fc4c57ebab2593562d52c61c5eb8
    inputs
    {
        input
        {
            address 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
            previous_output
            {
                hash 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
                index 0
            }
            script "[30450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af6817401] [03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb
            script "dup hash160 [58b7a60f11a904feef35a639b6048de8dd4d9f1c] equalverify checksig"
            value 45000
        }
    }
    version 1
}
```
Notice that the endorsement script has been applied to `transaction.inputs[0].script` and that `transaction.hash` has been updated.

**Validate** the endorsement of the transaction's first input, using the public key, previous output script, endorsement and transaction (optional).
```sh
$ bx input-validate 03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31 "dup hash160 [c564c740c6900b93afc9f1bdaef0a9d466adf6ee] equalverify checksig" 30450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af6817401 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c000000006b4830450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af68174012103e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
The endorsement is valid.
```
**Validate** the transaction against the blockchain (optional).
```sh
$ bx validate-tx 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c000000006b4830450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af68174012103e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
The transaction is valid.
```
**Broadcast** the transaction to the blockchain.
```sh
$ bx send-tx 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c000000006b4830450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af68174012103e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
Sent transaction at 2014-Oct-23 00:08:49.
```
### Confirm Spend of Bitcoin
Look up the **balance** of the sender address.
```sh
$ bx fetch-balance 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
```
```js
balance
{
    address 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
    confirmed 0
    received 100000
    unspent 0
}
```
Notice that the confirmed value has been reduced by the amount spent, to zero. This is because the amount is no longer confirmed to the address. Received is not reduced by spends, and so remains unchanged. Unspent is received minus the cumulative amount spent.
### View History of Spend
Look up the **history** for the address.
```sh
$ bx fetch-history 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
```
```js
transfers
{
    transfer
    {
        received
        {
            hash 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
            height 326392
            index 0
        }
        spent
        {
            hash 37c9c4ee0e84c7c7924f74d92cf0779ec6e8fc4c57ebab2593562d52c61c5eb8
            height 326581
            index 0
        }
        value 100000
    }
}
```
The amount previously received has been spent.
### Determine Spend Confirmation Level
Look up the current **blockchain height**.
```sh
$ bx fetch-height
```
```
326590
```
Using `transfers[0].spent.height`, there are currently `326590 - 326581 = 9` confirmations for the transaction.

View the [spend transaction](https://blockchain.info/tx/37c9c4ee0e84c7c7924f74d92cf0779ec6e8fc4c57ebab2593562d52c61c5eb8) on blockchain.info.