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

> The number of transactions matching a given prefix will increase over time.