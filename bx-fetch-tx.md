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
[first transaction](https://blockchain.info/tx/4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b) on the blockchain
```sh
$ bx fetch-tx 4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b
```
```
01000000010000000000000000000000000000000000000000000000000000000000000000ffffffff4d04ffff001d0104455468652054696d65732030332f4a616e2f32303039204368616e63656c6c6f72206f6e206272696e6b206f66207365636f6e64206261696c6f757420666f722062616e6b73ffffffff0100f2052a01000000434104678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5fac00000000
```
### Example 2
piped commands, decoding [Satoshi's words](http://www.thetimes.co.uk/tto/business/industries/banking/article2160028.ece)
```sh
$ bx fetch-tx 4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b | bx base16-decode
```
```
01000000010000000000000000000000000000000000000000000000000000000000000000ffffffff4d04ffff001d0104455468652054696d65732030332f4a616e2f32303039204368616e63656c6c6f72206f6e206272696e6b206f66207365636f6e64206261696c6f757420666f722062616e6b73ffffffff0100f2052a01000000434104678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5fac00000000
ÿÿÿÿMÿÿEThe Times 03/Jan/2009 Chancellor on brink of second bailout for banksÿÿÿÿò*CAgŠý°þUH'gñ¦q0·\Ö¨(à9	¦ybàêaÞ¶Iö¼?Lï8ÄóUåÁÞ\8M÷ºWŠLp+kñ_¬
```
### Example 3
--format json
```sh
$ bx fetch-tx -f json 4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b
```
```js
{
    "transaction": {
        "hash": "4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b",
        "inputs": {
            "input": {
                "previous_output": {
                    "hash": "0000000000000000000000000000000000000000000000000000000000000000",
                    "index": "4294967295"
                },
                "script": "[ 04ffff001d0104455468652054696d65732030332f4a616e2f32303039204368616e63656c6c6f72206f6e206272696e6b206f66207365636f6e64206261696c6f757420666f722062616e6b73 ]",
                "sequence": "4294967295"
            }
        },
        "lock_time": "0",
        "outputs": {
            "output": {
                "address": "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa",
                "script": "[ 04678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5f ] checksig",
                "value": "5000000000"
            }
        },
        "version": "1"
    }
}
```
From `transaction.inputs.input.script` above:
```sh
$ bx base16-decode 04ffff001d0104455468652054696d65732030332f4a616e2f32303039204368616e63656c6c6f72206f6e206272696e6b206f66207365636f6e64206261696c6f757420666f722062616e6b73 
```
```
ÿÿEThe Times 03/Jan/2009 Chancellor on brink of second bailout for banks
```