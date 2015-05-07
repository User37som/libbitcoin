This example is a continuation of [How to Create a Multisig Address](How-to-Create-a-Multisig-Address).

Send 0.001 bitcoins (100000 satoshis) to the multisig address using any Bitcoin wallet.

View the [transaction](https://blockchain.info/tx/f759759bc998ec96879e4ae8c1639e8a186e0d507401eb32e4479de64d340605) on blockchain.info.

### Confirm Receipt of Bitcoin
Look up the **balance** of the address.
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

