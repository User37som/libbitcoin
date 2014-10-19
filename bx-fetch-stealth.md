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
$ bx fetch-stealth 10101010
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
}
```