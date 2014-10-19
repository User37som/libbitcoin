Get the balance in satoshi of one or more Bitcoin addresses.
```sh
$ bx fetch-balance --help
```
```
Usage: bx fetch-balance [-h] [--config VALUE] [--format VALUE]           
[BITCOIN_ADDRESS]...                                                     

Info: Get the balance in satoshi of one or more Bitcoin addresses.       
Requires an Obelisk server connection.                                   

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'json', 'xml', 'info'
                     or 'native', defaults to native.                    
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BITCOIN_ADDRESS      The set of Bitcoin addresses. If not specified the  
                     addresses are read from STDIN.
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
    received 6538241483
    unconfirmed 6538241483
    confirmed 1538241483
}
```

> These numeric values will change over time as more people send money to Satoshi, and/or the money at this address is spent.

### Example 2
--format json
```sh
$ bx fetch-balance -f json 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```sh
{
    "balance": {
        "address": "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa",
        "received": "6538241483",
        "unconfirmed": "6538241483",
        "confirmed": "1538241483"
    }
}
```
### Example 3
--format xml
```sh
$ bx fetch-balance -f xml 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```xml
<?xml version="1.0" encoding="utf-8"?>
<balance><address>1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa</address><received>6538241483</received><unconfirmed>6538241483</unconfirmed><confirmed>1538241483</confirmed></balance>
```
### Example 4
multiple addresses
```sh
$ bx fetch-balance -f xml 134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz 13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe
```
```xml
<?xml version="1.0" encoding="utf-8"?>
<balance><address>13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe</address><received>90000</received><unconfirmed>90000</unconfirmed><confirmed>90000</confirmed></balance>
<?xml version="1.0" encoding="utf-8"?>
<balance><address>134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz</address><received>100000</received><unconfirmed>0</unconfirmed><confirmed>0</confirmed></balance>
```

> Notice that each result produces an independent XML (or JSON/INFO) document.