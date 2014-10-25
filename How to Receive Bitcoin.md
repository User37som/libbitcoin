Generate a **private key** from a random **seed** value.
```sh
$ bx seed | bx ec-new
```
```
dbcd61584666028ac88798bacdc76f4b (seed)
4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 (private key)
```
Create a Bitcoin **address** from the private key.
```sh
$ bx ec-to-public 4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 | bx ec-to-address
```
```
03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31 (public key)
1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6 (address)
```
Determine the number of **satoshis** in 0.001 bitcoins.
```sh
$ bx btc-to-satoshi 0.001
```
```
100000
```
Send 0.001 bitcoins (100000 satoshis) to the address using any Bitcoin wallet.
### Confirm Receipt of Bitcoin
Look up the **balance** of the address.
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
### View History of Receipt
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
        value 100000
    }
}
```
The value of `transfers[0].received.hash` should match the transaction identifier shown by your wallet.

Notice that `transfers[0].received.height` shows that the transaction now has at least one confirmation.
### Determine Receipt Confirmation Level
Look up the current **blockchain height**.
```sh
$ bx fetch-height
```
```
326525
```
Using `transfers[0].received.height`, there are currently `326525 - 326392 = 133` confirmations for the transaction.

View the [receive transaction](https://blockchain.info/tx/7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d) on blockchain.info.

This example is a continued in [How to Spend Bitcoin](How-to-Spend-Bitcoin).