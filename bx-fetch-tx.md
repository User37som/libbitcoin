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
The native transaction format is base16. This allows the output of `fetch-tx` to be piped into other commands.
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
--format json, decoding [Satoshi's words](http://www.thetimes.co.uk/tto/business/industries/banking/article2160028.ece)
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
### Example 4
--format info, [first WikiLeaks transaction](https://blockchain.info/tx/4eed9092aaf8cc8a527570546816a752d5fe825244c25c8e26084fc80b06b588)
```sh
$ bx fetch-tx -f info 4eed9092aaf8cc8a527570546816a752d5fe825244c25c8e26084fc80b06b588
```
```js
transaction
{
    hash 4eed9092aaf8cc8a527570546816a752d5fe825244c25c8e26084fc80b06b588
    inputs
    {
        input
        {
            address 136Zngm3jPWjXr62D6aAqiHViwC8GX7KrT
            previous_output
            {
                hash e58f3fb6e2ebe8e74e5af032dfd8c8e5e51f53d59489591a71599a80bdca910d
                index 0
            }
            script "[ 304502210092947e1d588378cd215c2d3990b862cf368657741b5941c3cadf87a46b5a211d02205ef4ba2c1f35886e4272250a2abec2d1f2f21d5c581bf3eb5fc27b5be332660701 ] [ 04aefca2b53d176aa22f730a5497eb32011e15387c63a75780efeb21e981e9728033808732a321b48a8e0e2a5f9c1efb745dd41e9c92c6260daad567544b122446 ]"
            sequence 4294967295
        }
        input
        {
            address 16twDP2ZL2nZTRsWmfpNrgs9PNDECyBJEV
            previous_output
            {
                hash 203609ba699c1f56e4a8d793a8cd746aa5aa5fc2e71205cf67a94487b45bafa9
                index 1
            }
            script "[ 3045022100b7e63179ce698082c0f97c4ba6e24f5c7b7d37e5098c1b46674d03ef17a68b8d022008ebc699df19f11a11e76320719d7c139bb10ce9aa255f674a44b95f54053d9d01 ] [ 04c8f5fbadfe4534eaa3e2ec49dd797aaa43cb13d669dbd6ab769ea45a5ebcdacc6aee8e0e75fec2cb7fa088e16ead1a979f394b5af9e0d2998b6dc5bb6c41b005 ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1HB5XMLmzFVj8ALj6mfBsbifRoD4miY36v
            script "dup hash160 [ b169f2b0b866db05900b93a5d76345f18d3afb24 ] equalverify checksig"
            value 7500000
        }
        output
        {
            address 16kZCdRoVmv9aWXagqxqm5NbLm19mQTr1V
            script "dup hash160 [ 3f156517411bd0ea2f22e2f42d6846b405facb27 ] equalverify checksig"
            value 97317
        }
    }
    version 1
}
```
### Example 5
very large transaction, [DPR Seized Coins #1](https://blockchain.info/address/1FfmbHfnpaZjKFvyi1okTjJJusN455paPH) 
```sh
$ bx fetch-tx -f info e3d6fe810f79b293705ed6e587951332c545a87fac860278b2ad4447106bb789 | more
```
```
transaction
{
    hash e3d6fe810f79b293705ed6e587951332c545a87fac860278b2ad4447106bb789
    inputs
    {
        input
        {
            address 1P7VNcDJ3VbUWqrUMZatR6kzEGAN7Fb5x7
            previous_output
            {
                hash 5362bffcc2e3cc4bfe8c80818d32dc9412ebe02df4509b1ed5800bab85175b28
                index 201
            }
            script "[ 3044022021b86b3cfd6d2f8147f6e3d8ed252d9d4cbf9e71b0a73a5c85bbb5894c369f8402203a39db8c1ae408fbecdef27065e8520b247035bd1bd37b48da49754a554bb62a01 ] [ 0480cff62d6af1c155c19f46d66a31770de29371bf09ae75e8eff41bcfd66a5da75e855911600506f7d54a7d3c89cbc342d15d670e982ba57a930a3dfa4be2780a ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 16sozEP1uBvVALtZzTSZ2gAs2sN7ERqKLa
            script "dup hash160 [ 4074a649949ca413afbdf9c5a8ef5bdc58e73bc8 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1K6XwLRysBbHTwqAU3mYMSv9GDLbYePiah
            script "dup hash160 [ c67e2b2dafaf3bacdda6181de8f20f4aaa577808 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1GN7KnHXktvwG97vTbyDBedPih4kGAbAXL
            script "dup hash160 [ a887e69af68d0393e35afdfd1bfdd66ed5e7e800 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 17LqrXSDFxyBQEgzQiiCXB4B7X94aX8QWZ
            script "dup hash160 [ 4591706b5215c507c90d6047e31a75f324da944a ] equalverify checksig"
            value 1111
        }
        output
        {
            address 12Eur7qR8H7WRqQcrLCZNV4oa7dp3zUvhF
            script "dup hash160 [ 0d99a5caa950cd4fb9f07b78ea028255ef31d4e3 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 138JzzviNVSH5Red9sjBk4YoqBaTrdT6JL
            script "dup hash160 [ 1752305d647021433f58df6e11b9259ff64743fc ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1gDw3uNGStrwRQhQuN1yC6Y7PifXVd13L
            script "dup hash160 [ 076b047bcde517eaae20aaa3b1d768fd9c7c61d1 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1QCkF8EmZkdS65RVp1nNm6R5sr911eRJLo
            script "dup hash160 [ fe8391055dfe99b3b0b99cad0f3c13ef6b108b09 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1BQn2bKKPmGQgbiMDVzQ13M5tDD54GB5LQ
            script "dup hash160 [ 723069772f67e106c250336d0725003802411c6b ] equalverify checksig"
            value 1111
        }
        output
        {
            address 15QAhZ7a8kzmwt5gXDbw3F83giSkxRXy81
            script "dup hash160 [ 30422aaf9741aa4ae91b22c248e762a519726cbf ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1GfbB6PbYVMXWWtYKFx9f6bvNJZLdMRngD
            script "dup hash160 [ abd63867f9be9b55ceb7f54f0b69af676f1844b6 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1Mo911Q5VDawyBKzANn1msDqZGETM8WZGC
            script "dup hash160 [ e41c53fd11d6aeb0d69bb47022615e9370d1769f ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1QD2qgdZb9mp5E6QCo1NbYs7qgwW6iXM9s
            script "dup hash160 [ fe916b84c35251c9df346316b0d0fb7daed7be3c ] equalverify checksig"
            value 1111
        }
        output
        {
            address 19JdWLNwVdhs2gYu9eXp8xs26QA3fMy9ZH
            script "dup hash160 [ 5b168d148d746b43145aba7d193be4baa7223bfb ] equalverify checksig"
            value 1111
        }
        output
        {
            address 16fmwnm5oVBuCrqScWVbBq8HXxsRAkdYCU
            script "dup hash160 [ 3e2df40f7346e1524cf63c10f472edd8df21798d ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1N8LSwn7jGiy3YQFC9Wj2mo65RDchJEa6H
            script "dup hash160 [ e7bdc978882731ad6dc7b74bc49ca6d6a2a3f207 ] equalverify checksig"
 transaction
{
    hash e3d6fe810f79b293705ed6e587951332c545a87fac860278b2ad4447106bb789
    inputs
    {
        input
        {
            address 1P7VNcDJ3VbUWqrUMZatR6kzEGAN7Fb5x7
            previous_output
            {
                hash 5362bffcc2e3cc4bfe8c80818d32dc9412ebe02df4509b1ed5800bab85175b28
                index 201
            }
            script "[ 3044022021b86b3cfd6d2f8147f6e3d8ed252d9d4cbf9e71b0a73a5c85bbb5894c369f8402203a39db8c1ae408fbecdef27065e8520b247035bd1bd37b48da49754a554bb62a01 ] [ 0480cff62d6af1c155c19f46d66a31770de29371bf09ae75e8eff41bcfd66a5da75e855911600506f7d54a7d3c89cbc342d15d670e982ba57a930a3dfa4be2780a ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 16sozEP1uBvVALtZzTSZ2gAs2sN7ERqKLa
            script "dup hash160 [ 4074a649949ca413afbdf9c5a8ef5bdc58e73bc8 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1K6XwLRysBbHTwqAU3mYMSv9GDLbYePiah
            script "dup hash160 [ c67e2b2dafaf3bacdda6181de8f20f4aaa577808 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1GN7KnHXktvwG97vTbyDBedPih4kGAbAXL
            script "dup hash160 [ a887e69af68d0393e35afdfd1bfdd66ed5e7e800 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 17LqrXSDFxyBQEgzQiiCXB4B7X94aX8QWZ
            script "dup hash160 [ 4591706b5215c507c90d6047e31a75f324da944a ] equalverify checksig"
            value 1111
        }
        output
        {
            address 12Eur7qR8H7WRqQcrLCZNV4oa7dp3zUvhF
            script "dup hash160 [ 0d99a5caa950cd4fb9f07b78ea028255ef31d4e3 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 138JzzviNVSH5Red9sjBk4YoqBaTrdT6JL
            script "dup hash160 [ 1752305d647021433f58df6e11b9259ff64743fc ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1gDw3uNGStrwRQhQuN1yC6Y7PifXVd13L
            script "dup hash160 [ 076b047bcde517eaae20aaa3b1d768fd9c7c61d1 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1QCkF8EmZkdS65RVp1nNm6R5sr911eRJLo
            script "dup hash160 [ fe8391055dfe99b3b0b99cad0f3c13ef6b108b09 ] equalverify checksig"
            value 1111
        }
        output
        {
            address 1BQn2bKKPmGQgbiMDVzQ13M5tDD54GB5LQ
            script "dup hash160 [ 723069772f67e106c250336d0725003802411c6b ] equalverify checksig"
            value 1111
        }
        output
        {
            address 15QAhZ7a8kzmwt5gXDbw3F83giSkxRXy81
            script "dup hash160 [ 30422aaf9741aa4ae91b22c248e762a519726cbf ] equalverify checksig"
-- More  -- 
```