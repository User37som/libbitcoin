### Confirm a Payment
Generate a private key from a random seed value.
```sh
$ bx seed | bx ec-new
```
```
dbcd61584666028ac88798bacdc76f4b (seed)
4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 (private key)
```
Create a Bitcoin address from the private key.
```sh
$ bx ec-to-public 4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 | bx ec-to-address
```
```
03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31 (public key)
1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6 (bitcoin address)
```
Determine the number of satoshis in 0.001 bitcoins.
```sh
$ bx btc-to-satoshi 0.001
```
```
100000
```
Send 0.001 bitcoins (100000 satoshis) to the address using any wallet.

Look up the balance of the address.
```sh
$ bx fetch-balance 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
```
```js
balance
{
    address 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
    confirmed 0
    received 100000
    unspent 100000
}
```
Notice that `balance.confirmed` shows that the transaction has no confirmations.

Look up the history for the address.
```sh
$ bx fetch-history 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
```
```js
transfers
{
    transfer
    {
        output
        {
            hash 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
            height 326392
            index 0
        }
        value 100000
    }
}
```
The value of `transfers.transfer.output.hash` should match the transaction identifier shown by your wallet.

Notice that `transfers.transfer.output.height` shows that the transaction now has at least one confirmation.

Look up the transaction by its hash.
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
            script "[ 304502206be979f1f89776e26abb40f458dc942d191d447cf3ce847d2d7e430df6b21ac4022100cade875670d71bd972f151b00544044d90a75261a9a01542968a1b36b31aea1801 ] [ 041fd7ca20852f638e82ac43b2df2ac7b38a3fec1622fb33c9f679ae909868a7e6e013429b2421a871a4e1d5d5702bea978bdd8ec399657dc6f3c0334a83de40bf ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
            script "dup hash160 [ c564c740c6900b93afc9f1bdaef0a9d466adf6ee ] equalverify checksig"
            value 100000
        }
        output
        {
            address 18kn866ztW2Y12DkijCubQmE6xBqmJS4Gr
            script "dup hash160 [ 55106ed6c650e125c28f767c83ccfbc0c231fc8a ] equalverify checksig"
            value 328860000
        }
    }
    version 1
}
```
### Spend the Payment
Obtain an address to which the money will be sent, such as [Freenet](https://blockchain.info/address/1966U1pjj15tLxPXZ19U48c99EJDkdXeqb).
```
1966U1pjj15tLxPXZ19U48c99EJDkdXeqb
```
The first output above will become the input to a new transaction. This input is described as `transaction hash:index`, where the index is zero-based.
```
7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d:0
```
The output for the new transaction is described as `address:amount`, where the amount is a number of satoshis. There are 100,000 satoshis available to spend, of which this transaction will spend 45% to Freenet.
```
1966U1pjj15tLxPXZ19U48c99EJDkdXeqb:45000
```
In this example the remainder will not be spent to any address. This will result in 55,000 satoshis being earned by miners as a transaction fee.

Construct the transaction from the inputs and outputs, in this case one of each.
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
            script "dup hash160 [ 58b7a60f11a904feef35a639b6048de8dd4d9f1c ] equalverify checksig"
            value 45000
        }
    }
    version 1
}
```
Notice that `transactions.inputs.input.script` is empty. This means that that input has not been signed.

Signing requires the private key `4ce3eb6b...` corresponding to the address `1JziqzXe...` of the previous output `7c3e880e...:0`.

Constructing a signature script for the transaction requires the hashed public key also corresponding to the address `1JziqzXe...`.

Decode the address.
```sh
$ bx address-decode 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
```
```js
wrapper
{
    checksum 3046565692
    payload c564c740c6900b93afc9f1bdaef0a9d466adf6ee
    version 0
}
```
Create a [public key script](https://en.bitcoin.it/wiki/Script#Scripts) using the `wrapper.payload`.
```js
"dup hash160 [ c564c740c6900b93afc9f1bdaef0a9d466adf6ee ] equalverify checksig"
```
Generate a random nonce for use in signing.
```sh
$ bx seed
```
```
707e3d717925ba2e98234dd6f3a38eb5
```
Create a signature for the first input of the new transaction.
```sh
$ bx input-sign 4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 707e3d717925ba2e98234dd6f3a38eb5 76a914c564c740c6900b93afc9f1bdaef0a9d466adf6ee88ac ... ...
```
```

```
Create a signature script and assign it to the new transaction input.
```sh
bx input-set "[ 30450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022071a0d1e7dd23492df67275d2464922ff6f658d532fba4c0500f0dc8a0a1723f7 ] [ 03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31 ]"
```
```

```
Decode the transaction.
```sh
$ bx tx-decode 
```
```js

```