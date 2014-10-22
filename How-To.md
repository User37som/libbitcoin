# Offline Transactions
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

> Notice that `balance.confirmed` shows that the transaction has no confirmations.

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

> Notice that `transfers.transfer.output.height` shows that the transaction how has at least one confirmation.

```