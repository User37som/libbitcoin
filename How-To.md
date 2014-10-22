### Confirm a Payment
Generate a private key from a random seed value.
```sh
$ bx seed | bx ec-new
```
```
dbcd61584666028ac88798bacdc76f4b (seed)
4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 (private key)
```
Make a Bitcoin address from the private key.
```sh
$ bx ec-to-public 4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 | bx ec-to-address
```
```
03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31 (public key)
1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6 (bitcoin address)
```
Send some money (0.001 BTC) to the address using any wallet. Look up the balance of the address.
```sh
$ bx fetch-balance 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
```
```js
balance
{
    address 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
    received 100000
    unconfirmed 100000
    confirmed 0
}
```
Notice that `balance.confirmed` shows that the transaction has no confirmations.

The [address](https://blockchain.info/address/1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6) can be also located on blockchain.info.

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

The [transaction](https://blockchain.info/tx/7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d) can also be located on blockchain.info.

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
Obtain an address to which the money will be sent, such as [DarkWallet](https://blockchain.info/address/31oSGBBNrpCiENH3XMZpiP6GTC4tad4bMy).
```
31oSGBBNrpCiENH3XMZpiP6GTC4tad4bMy
```
The output identified above as `transfers.transfer.output` will become the input to a new transaction. The input is described as follows.
```
7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d:0
```