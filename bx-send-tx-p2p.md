Broadcast a transaction to the Bitcoin network via the Bitcoin peer-to-peer network.
```sh
$ bx send-tx-p2p --help
```
```
Usage: bx send-tx-p2p [-h] [--config VALUE] [--nodes VALUE] [TRANSACTION]

Info: Broadcast a transaction to the Bitcoin network via the Bitcoin     
peer-to-peer network.                                                    

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-n [--nodes]         The number of network nodes to send the transaction 
                     to, defaults to two.                                

Arguments (positional):

TRANSACTION          The Base16 transaction to send. If not specified the
                     transaction is read from STDIN.
```
### Example 1
```sh
$ bx send-tx-p2p 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970100000069463044022039a36013301597daef41fbe593a02cc513d0b55527ec2df1050e2e8ff49c85c202204fcc407ce9b6f719ee7d009aeb8d8d21423f400a5b871394ca32e00c26b348dd2103c40cbd64c9c608df2c9730f49b0888c4db1c436e8b2b74aead6c6afbd10428c0ffffffff01905f0100000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000
```
```
0 connections.
Started.
Sending 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970100000069463044022039a36013301597daef41fbe593a02cc513d0b55527ec2df1050e2e8ff49c85c202204fcc407ce9b6f719ee7d009aeb8d8d21423f400a5b871394ca32e00c26b348dd2103c40cbd64c9c608df2c9730f49b0888c4db1c436e8b2b74aead6c6afbd10428c0ffffffff01905f0100000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000.
Sent at 2014-Oct-20 01:13:15.
```