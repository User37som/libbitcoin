Get the balance in satoshi of a payment address.
```sh
$ bx fetch-balance --help
```
```
Usage: bx fetch-balance [-h] [--config VALUE] [--format VALUE]           
[PAYMENT_ADDRESS]                                                        

Info: Get the balance in satoshi of a payment address. Requires a        
Libbitcoin server connection.                                    

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json', and  
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

PAYMENT_ADDRESS      The payment address. If not specified the address is
                     read from STDIN.
```
This command supports [configuration settings](Configuration-Settings).

Version 3 (and later) does not provide unconfirmed balance. A confirmation of at least one block on the strong chain is required for a value to be included.

A value of 18446744073709551615 indicates that a spend is uncorrelated to a receipt. This will occur if the spend is indexed but the receipt is not, which can occur if the server is configured to start indexing at a height between the two transactions. Correlation failure can also occur due to an extremely low probability hash collision (1 in 2^49). The caller should always check for this condition.

### Example 1
[first address](https://blockchain.info/address/1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa) on the blockchain
```sh
$ bx fetch-balance 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```
balance
{
    address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
    received 6538241483
    spent 0
}
```

The above properties represent the number of satoshis associated with the address.

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
        "received": "100000",
        "spent": "100000",
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
<balance><address>13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe</address><received>90000</received><spent>0</spent></balance>
```