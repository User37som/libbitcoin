Broadcast a transaction to the Bitcoin network via a single Bitcoin network node.
```sh
$ Usage: bx send-tx-node [-h] [--config VALUE] [--port VALUE] [--host      
VALUE] [TRANSACTION]                                                     
```
```
Info: Broadcast a transaction to the Bitcoin network via a single Bitcoin
network node.                                                            

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-p [--port]          The IP port of the Bitcoin service on the node.     
                     Defaults to 8333, the standard for mainnet.         
-t [--host]          The IP address or DNS name of the node. Defaults to 
                     localhost.                                          

Arguments (positional):

TRANSACTION          The Base16 transaction to send. If not specified the
                     transaction is read from STDIN.
```
Broadcasting a transaction offers no acceptance or propagation guarantees.

This command writes to the configured [log files](Log-Files).
### Example 1
no bitcoind on localhost:8333
```sh
$ bx send-tx-node 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970100000069463044022039a36013301597daef41fbe593a02cc513d0b55527ec2df1050e2e8ff49c85c202204fcc407ce9b6f719ee7d009aeb8d8d21423f400a5b871394ca32e00c26b348dd2103c40cbd64c9c608df2c9730f49b0888c4db1c436e8b2b74aead6c6afbd10428c0ffffffff01905f0100000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000
```
```
Unable to reach remote network
```
### Example 2
bitcoind on localhost:8333
```sh
$ bx send-tx-node 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970100000069463044022039a36013301597daef41fbe593a02cc513d0b55527ec2df1050e2e8ff49c85c202204fcc407ce9b6f719ee7d009aeb8d8d21423f400a5b871394ca32e00c26b348dd2103c40cbd64c9c608df2c9730f49b0888c4db1c436e8b2b74aead6c6afbd10428c0ffffffff01905f0100000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000
```
```
Sent transaction at 2014-Oct-20 01:17:55.
```
### Example 3
--host 127.0.0.1, --port 8333
```sh
$ bx send-tx-node -t 127.0.0.1 -p 8333 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970100000069463044022039a36013301597daef41fbe593a02cc513d0b55527ec2df1050e2e8ff49c85c202204fcc407ce9b6f719ee7d009aeb8d8d21423f400a5b871394ca32e00c26b348dd2103c40cbd64c9c608df2c9730f49b0888c4db1c436e8b2b74aead6c6afbd10428c0ffffffff01905f0100000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000
```
```
Sent transaction at 2014-Oct-20 01:34:10.
```