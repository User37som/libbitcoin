Broadcast a transaction to the Bitcoin network via an Obelisk server.
```sh
$ bx send-tx --help
```
```
Usage: bx send-tx [-h] [--config VALUE] [TRANSACTION]                    

Info: Broadcast a transaction to the Bitcoin network via an Obelisk      
server.                                                                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

TRANSACTION          The Base16 transaction to send. If not specified the
                     transaction is read from STDIN. 
```
This command supports [configuration settings](Configuration-Settings).
### Example 1
```sh
$ bx send-tx 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970100000069463044022039a36013301597daef41fbe593a02cc513d0b55527ec2df1050e2e8ff49c85c202204fcc407ce9b6f719ee7d009aeb8d8d21423f400a5b871394ca32e00c26b348dd2103c40cbd64c9c608df2c9730f49b0888c4db1c436e8b2b74aead6c6afbd10428c0ffffffff01905f0100000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000
```
```
Sent transaction at 2014-Oct-20 00:51:55.
```