Get the balance in satoshi of a Bitcoin address.
```sh
$ bx fetch-balance --help
```
```
Usage: bx fetch-balance [-h] [--config VALUE] [--format VALUE]           
[BITCOIN_ADDRESS]                                                        

Info: Get the balance in satoshi of a Bitcoin address. Requires an       
Obelisk server connection.                                               

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json', and  
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BITCOIN_ADDRESS      The Bitcoin address. If not specified the address is
                     read from STDIN.
```
### Example 1
[first address](https://blockchain.info/address/1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa) on the blockchain
```sh
$ bx fetch-balance 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```js
balance
{
    address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
    confirmed 1538241483
    received 6538241483
    unspent 6538241483
}
```

The following properties represent a number of satoshis associated with the address in the following manner.
* confirmed: The number with at least one confirmation, excluding those spent.
* received: The number confirmed or unconfirmed, including those spent.
* unspent: The number received that remain unspent.

> These numeric values will change over time as more people send money to Satoshi, and/or the money at this address is spent. This first transaction is unique in that it contains [50 bitcoin that can never be confirmed](https://en.bitcoin.it/wiki/Genesis_block).

### Example 2
--format json
```sh
$ bx fetch-balance -f json 134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz
```
```js
{
    "balance": {
        "address": "134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz",
        "confirmed": "0"
        "received": "100000",
        "unspent": "0",
    }
}
```
### Example 3
--format xml
```sh
$ bx fetch-balance -f xml 13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe
```
```xml
<?xml version="1.0" encoding="utf-8"?>
<balance><address>13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe</address><confirmed>90000</confirmed><received>90000</received><unspent>90000</unspent></balance>
```