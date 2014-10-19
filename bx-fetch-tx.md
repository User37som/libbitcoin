Get transactions by hash.
```sh
$ bx fetch-tx --help
```
```
Usage: bx fetch-tx [-h] [--config VALUE] [--format VALUE] [HASH]...      

Info: Get transactions by hash. Requires an Obelisk server connection.   

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'json', 'xml', 'info'
                     or 'native', defaults to native.                    
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

HASH                 The set of Base16 transaction hashes of transactions
                     to get. If not specified the transaction hashes are 
                     read from STDIN.
```
### Example 1
[first transaction](https://blockchain.info/tx/4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b)
```sh
$ bx fetch-tx 4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b
```
```
01000000010000000000000000000000000000000000000000000000000000000000000000ffffffff4d04ffff001d0104455468652054696d65732030332f4a616e2f32303039204368616e63656c6c6f72206f6e206272696e6b206f66207365636f6e64206261696c6f757420666f722062616e6b73ffffffff0100f2052a01000000434104678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5fac00000000
```