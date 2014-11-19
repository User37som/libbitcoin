Watch the network for transactions in which an address participates.
```sh
$ bx watch-address --help
```
```
Usage: bx watch-address [-h] [--config VALUE] [--format VALUE]           
[BITCOIN_ADDRESS]                                                        

Info: Watch the network for transactions in which an address             
participates. Requires an Obelisk server connection.                     

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BITCOIN_ADDRESS      The participating Bitcoin address. If not specified 
                     the address is read from STDIN. 
```
This command reflects transactions created after the subscription is established.

This command supports [configuration settings](Configuration-Settings).

> Type `ctrl-c` to terminate the watcher.

### Example 1
monitor donations to Satoshi
```sh
$ bx watch-address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
This message will be written once the subscription is established.
```
Watching address: 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa...
```
For each new transaction that impacts the address a new `watch_address` will be written.
```sh
watch_address
{
    block 0000000000000000013aeff116df0b35ce5b98a3ef1880289323050858fe838e
    address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
    transaction
    {
        hash 6c62836aed69af34fd418fae95de05c3aace0c2d3cc495c110e30753ddfae19d
        inputs
        {
            input
            {
                address 1J8dQ4epAWYUpfyewRifQrhg7hKtC6YbcZ
                previous_output
                {
                    hash d4cf7c9f93664632974796e22eeb935ceabef873634124eac25bce0c6a45ebf2
                    index 1
                }
                script "[ 3044022062b2caeee469b62ef82f4e60abb7bf5f852b71f7311a42efb025f5356d4d6b5102203096d6623a321eb5463fdbf3e4fb5e7cb753bfb3cdeb5ee866cac6f35e80fd6901 ] [ 04c0b9cdea65ef7d4c01b236afaccc652f1d2f0f5dbab611303bf1552adaeed6b83e0b52f67409944267bc27635f611fbc0c50f17db15b4daff2959137576920dc ]"
                sequence 4294967295
            }
        }
        lock_time 0
        outputs
        {
            output
            {
                address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
                script "dup hash160 [ 62e907b15cbf27d5425399ebf6f0fb50ebb88f18 ] equalverify checksig"
                value 82940
            }
            output
            {
                address 1H2in1HxEzSKHssPtog2krjFPiPfrKSiw4
                script "dup hash160 [ afd54d22895cef79d4d0133795c5229e673dd5e5 ] equalverify checksig"
                value 1826990
            }
        }
        version 1
    }
}
watch_address
{
    block 0000000000000000013aeff116df0b35ce5b98a3ef1880289323050858fe838e
    address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
    transaction
    {
        hash 049e269ce20e492197dc13e837e42f63ddf96445e53556e1364a9b66e8fb84db
        inputs
        {
            input
            {
                address 1H2in1HxEzSKHssPtog2krjFPiPfrKSiw4
                previous_output
                {
                    hash 6c62836aed69af34fd418fae95de05c3aace0c2d3cc495c110e30753ddfae19d
                    index 1
                }
                script "[ 304502202d7ac7e759140e8cfb4a54125d32c6895f10c652b9b9dd00fea9cf2c84e4d0e5022100f1d776c8ed802c2f28b35f5e4c7cc19892dd10f25172ce174ea0b282b5c0557801 ] [ 0422e9be731202c691e0b8eeceec9b2b67755fded97ac7ab10ecd1beb58ca9ce9623045c89cfe9e6b3f12da6f04ada3f06eeb026740601df6853711091127f3802 ]"
                sequence 4294967295
            }
        }
        lock_time 0
        outputs
        {
            output
            {
                address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
                script "dup hash160 [ 62e907b15cbf27d5425399ebf6f0fb50ebb88f18 ] equalverify checksig"
                value 82940
            }
            output
            {
                address 1Ak8VwX6x4FPbA6aXTC3BQGQHnnhfaJuB8
                script "dup hash160 [ 6ae1473a340fb93110e1ea9d332bdfcbb0f364a5 ] equalverify checksig"
                value 1724050
            }
        }
        version 1
    }
}
watch_address
{
    block 0000000000000000000000000000000000000000000000000000000000000000
    address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
    transaction
    {
        hash 010f49298a5f122cb06abfff460847cc3e2c427ff8eafda52776cb2211f0d3d5
        inputs
        {
            input
            {
                address 129sBvF6Jternwdn5XcoA37LinQRcmAD5U
                previous_output
                {
                    hash 2969f08de39989ac352a893dc048d74b55459ee97f7cb391fdde17ff4ef11d30
                    index 0
                }
                script "[ 304402203ec32fa9023cc964191886913d67fe45589944b8a3156e8fd7ef7129af0750190220745c51707b32725ee0ef2b2810d806ca1e5a7f7d0a1b15bdf6957cca6ca6165201 ] [ 04146c664fa851cc33ea2c762ad5eb3dc6d7c061ca7d75cb0b04ed5dcea810277ceaa5ca39b48f106d866e26003a2becb949afe737aa72af857db18058e79bb227 ]"
                sequence 4294967295
            }
        }
        lock_time 0
        outputs
        {
            output
            {
                address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
                script "dup hash160 [ 62e907b15cbf27d5425399ebf6f0fb50ebb88f18 ] equalverify checksig"
                value 10000
            }
            output
            {
                address 1CR6Go9LYA4nj4pwZVDkrDpGMngkqG672K
                script "dup hash160 [ 7d37c49086c561414101e338ac8f6ddbafc058cf ] equalverify checksig"
                value 99970000
            }
        }
        version 1
    }
}
```

> Notice that the last transaction is unconfirmed and therefore shows up in block `0000000000000000000000000000000000000000000000000000000000000000`. The other transactions are both shown in block `0000000000000000013aeff116df0b35ce5b98a3ef1880289323050858fe838e`, which was the most recent block at the time.