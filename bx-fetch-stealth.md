Get metadata on potential payment transactions by stealth prefix.
```sh
$ bx fetch-stealth --help
```
```
Usage: bx fetch-stealth [-h] [--config VALUE] [--format VALUE] [--height 
VALUE] [PREFIX]                                                          

Info: Get metadata on potential payment transactions by stealth prefix.  
Requires an Obelisk server connection.                                   

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'json', 'xml', 'info'
                     or 'native', defaults to native.                    
-h [--help]          Get a description and instructions for this command.
-t [--height]        The minimum block height of transactions to include.

Arguments (positional):

PREFIX               The Base2 stealth prefix used to locate             
                     transactions. Defaults to all stealth transactions.
```
The number of transactions matching a given prefix will increase over time.
### Example 1
```sh
$ bx fetch-stealth 101010
```
```js
stealth
{
    match
    {
        ephemeral_public_key 03c35235b93427c39f477a83c493d2ea74d9195dc8a3b3e7dbb5ad88584b1472d2
        paid_address 1C8cs6vuuHqN7dtHqh13Yc6395unYcpSC6
        transaction_hash d216cd6596d4119acba1b8d786cdeb15f76f01d8a3ee12603e2581950857b736
    }
    match
    {
        ephemeral_public_key 037d2dc47d2cdef67eb84996b9df9d91d66624651d4902b82b1655f884f871328d
        paid_address 1EokigXmAJsZarQ7v36BYxeSy16gAAvZW4
        transaction_hash d3bff487e6b74141653035f6318545b129ca519ee0fecb616cdf764899ad23ff
    }
    match
    {
        ephemeral_public_key 0307d4526afaa699eec1d4b53570d08f56d12f825079ffeda9f6f41aa6fc943613
        paid_address 13LVHNKKc3kZrFF28foBY4pXwovMiZQ6gY
        transaction_hash 0406227a7d441e776d67d723da08a2d0e39714d0eb07d927cbf45dee8a2a23b9
    }
    match
    {
        ephemeral_public_key 03a386356c978169f1af8c69c8aa6ae5932c27919f5ebb6e9f05d728df6913f700
        paid_address 14ZrpgUDPuAsVXcei35MRFTv6oCYmPc1uV
        transaction_hash 2b0580d7aaf27a231a3905d45c332ba2c17bef343304d7486429b6e5b14c0294
    }
}
```
### Example 2
--format json, --height 325500, prefix 01
```sh
$ bx fetch-stealth -f json -t 325500 01
```
```js
{
    "stealth": {
        "match": {
            "ephemeral_public_key": "022ec7cd1d0697e746c4044a4582db99ac85e9158ebd2c0fb2a797759ca418dd8d",
            "paid_address": "1GqSZbEXDQ98aDKhja33cAXRdT9Z8RhRuZ",
            "transaction_hash": "4e36b6ff5630631489ff40a18fe764051898ad032eb2e0a3af4c12c1e03475cc"
        }
    }
}
```

> Notice that the transaction [4e36b6ff...](https://blockchain.info/tx/4e36b6ff5630631489ff40a18fe764051898ad032eb2e0a3af4c12c1e03475cc) is identified with "Stealth Address Data".

### Example 3
pipe to file, all stealth transactions 
```sh
$ bx fetch-stealth -f xml > stealth.xml
```