Get enough unspent transaction outputs from a payment address to pay a number of satoshi.
```
$ bx fetch-utxo --help
```
```
Usage: bx fetch-utxo [-h] [--algorithm value] [--config value] [--format 
value] SATOSHI [PAYMENT_ADDRESS]                                         

Info: Get enough unspent transaction outputs from a payment address to   
pay a number of satoshi. Requires a Libbitcoin server connection.        

Options (named):

-a [--algorithm]     The algorithm for unspent output selection. Options 
                     are 'greedy' and 'individual', defaults to 'greedy' 
-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SATOSHI              The whole number of satoshi.                        
PAYMENT_ADDRESS      The payment address. If not specified the address is
                     read from STDIN.  
```
This command supports [configuration settings](Configuration-Settings).

### Example 1
Get the smallest unspent output for 
[1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa](https://blockchain.info/address/1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa) worth at least 400000000 satoshi.
```
$ bx fetch-utxo 400000000 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```
points
{
    point
    {
        hash db9e8d8a112437a5fc620c969cc76f3683e98475737c286d62002369f0f46fe5
        index 0
        value 400000000
    }
}
```
### Example 2
--algorithm individual

Get all individual unspent outputs of 
[1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa](https://blockchain.info/address/1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa) worth at least 123400000 satoshi.
```
$ bx fetch-utxo 123400000 -a individual 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```
points
{
    point
    {
        hash db9e8d8a112437a5fc620c969cc76f3683e98475737c286d62002369f0f46fe5
        index 0
        value 400000000
    }
}
```