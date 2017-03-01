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
[1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa](https://blockchain.info/address/1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa)
```
$ bx fetch-utxo 5500000000 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```
selection
{
    change 23456000
    points
    {
        points
        {
            hash 4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b
            index 0
        }
        points
        {
            hash db9e8d8a112437a5fc620c969cc76f3683e98475737c286d62002369f0f46fe5
            index 0
        }
        points
        {
            hash 0590c372e7b90c5cc17855ac444032ba7726eb559bb9cf488e38fa6cdc4fcc40
            index 0
        }
    }
}
```