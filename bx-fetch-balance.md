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
                     address is read from STDIN.
```
### Example 1
first address on the blockchain
```sh
$ bx fetch-balance 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```
address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
received 6538155229
unconfirmed 6538155229
confirmed 1538155229
```
### Example 2
--format json
```sh
$ bx fetch-balance -f json 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```sh
{
    "address": "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa",
    "received": "6538155229",
    "unconfirmed": "6538155229",
    "confirmed": "1538155229"
}
```
### Example 2
--format xml
```sh
$ bx fetch-balance -f xml 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```xml
<?xml version="1.0" encoding="utf-8"?>
<address>1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa</address><received>6538155229</received><unconfirmed>6538155229</unconfirmed><confirmed>1538155229</confirmed>
```