Get transactions by hash.
```sh
$ bx fetch-tx --help
```
```
Usage: bx fetch-tx [-h] [--config VALUE] [--format VALUE] [HASH]...      

Info: Get transactions by hash. Requires an Obelisk server connection.   

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json', and  
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

HASH                 The set of Base16 transaction hashes of transactions
                     to get. If not specified the transaction hashes are 
                     read from STDIN.
```
### Example 1
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
### Example 2
--format xml, [first WikiLeaks transaction](https://blockchain.info/tx/4eed9092aaf8cc8a527570546816a752d5fe825244c25c8e26084fc80b06b588)
```sh
$ bx fetch-tx -f xml 4eed9092aaf8cc8a527570546816a752d5fe825244c25c8e26084fc80b06b588
```
```xml
<?xml version="1.0" encoding="utf-8"?>
<transaction><hash>4eed9092aaf8cc8a527570546816a752d5fe825244c25c8e26084fc80b06b588</hash><inputs><input><address>136Zngm3jPWjXr62D6aAqiHViwC8GX7KrT</address><previous_output><hash>e58f3fb6e2ebe8e74e5af032dfd8c8e5e51f53d59489591a71599a80bdca910d</hash><index>0</index></previous_output><script>[ 304502210092947e1d588378cd215c2d3990b862cf368657741b5941c3cadf87a46b5a211d02205ef4ba2c1f35886e4272250a2abec2d1f2f21d5c581bf3eb5fc27b5be332660701 ] [ 04aefca2b53d176aa22f730a5497eb32011e15387c63a75780efeb21e981e9728033808732a321b48a8e0e2a5f9c1efb745dd41e9c92c6260daad567544b122446 ]</script><sequence>4294967295</sequence></input><input><address>16twDP2ZL2nZTRsWmfpNrgs9PNDECyBJEV</address><previous_output><hash>203609ba699c1f56e4a8d793a8cd746aa5aa5fc2e71205cf67a94487b45bafa9</hash><index>1</index></previous_output><script>[ 3045022100b7e63179ce698082c0f97c4ba6e24f5c7b7d37e5098c1b46674d03ef17a68b8d022008ebc699df19f11a11e76320719d7c139bb10ce9aa255f674a44b95f54053d9d01 ] [ 04c8f5fbadfe4534eaa3e2ec49dd797aaa43cb13d669dbd6ab769ea45a5ebcdacc6aee8e0e75fec2cb7fa088e16ead1a979f394b5af9e0d2998b6dc5bb6c41b005 ]</script><sequence>4294967295</sequence></input></inputs><lock_time>0</lock_time><outputs><output><address>1HB5XMLmzFVj8ALj6mfBsbifRoD4miY36v</address><script>dup hash160 [ b169f2b0b866db05900b93a5d76345f18d3afb24 ] equalverify checksig</script><value>7500000</value></output><output><address>16kZCdRoVmv9aWXagqxqm5NbLm19mQTr1V</address><script>dup hash160 [ 3f156517411bd0ea2f22e2f42d6846b405facb27 ] equalverify checksig</script><value>97317</value></output></outputs><version>1</version></transaction>
```
### Example 3
pipe to file, [DPR Seized Coins #1](https://blockchain.info/tx/e3d6fe810f79b293705ed6e587951332c545a87fac860278b2ad4447106bb789) 
```sh
$ bx fetch-tx -f xml e3d6fe810f79b293705ed6e587951332c545a87fac860278b2ad4447106bb789 > dpr1.xml
```