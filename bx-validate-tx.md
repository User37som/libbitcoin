Determine if a transaction is valid for submission to the blockchain.
```sh
$ bx validate-tx --help
```
```
Usage: bx validate-tx [-h] [--config VALUE] [TRANSACTION]                

Info: Determine if a transaction is valid for submission to the          
blockchain. Requires a Libbitcoin server connection.

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

TRANSACTION          The Base16 transaction. If not specified the        
                     transaction is read from STDIN.
```
This command supports [configuration settings](Configuration-Settings).
### Example 1
inputs invalid
```sh
$ bx validate-tx 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970100000069463044022039a36013301597daef41fbe593a02cc513d0b55527ec2df1050e2e8ff49c85c202204fcc407ce9b6f719ee7d009aeb8d8d21423f400a5b871394ca32e00c26b348dd2103c40cbd64c9c608df2c9730f49b0888c4db1c436e8b2b74aead6c6afbd10428c0ffffffff01905f0100000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000
```
```
Validation of inputs failed
```
There are several possible error messages. Success is indicated by either of the following two messages.
```
The transaction is valid.
```
```
The transaction is valid, with unconfirmed inputs at index: 0, 2.
```