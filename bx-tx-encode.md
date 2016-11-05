Encode an unsigned transaction as Base16.
```sh
$ bx tx-encode --help
```
```
Usage: bx tx-encode [-h] [--config VALUE] [--input VALUE] [--lock_time   
VALUE] [--output VALUE] [--script_version VALUE] [--version VALUE]       

Info: Encode an unsigned transaction as Base16.                          

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-i [--input]         The set of transaction input points encoded as      
                     TXHASH:INDEX:SEQUENCE. TXHASH is a Base16           
                     transaction hash. INDEX is the 32 bit input index in
                     the context of the transaction. SEQUENCE is the     
                     optional 32 bit input sequence and defaults to the  
                     maximum value.                                      
-l [--lock_time]     The transaction lock time.                          
-o [--output]        The set of transaction output data encoded as       
                     TARGET:SATOSHI:SEED. TARGET is an address (including
                     stealth or pay-to-script-hash) or a Base16 script.  
                     SATOSHI is the 64 bit spend amount in satoshi. SEED 
                     is required for stealth outputs and not used        
                     otherwise. The same seed should NOT be used for     
                     multiple outputs.                                   
-s [--script_version] The pay-to-script-hash payment address version,     
                     defaults to 5. This is used to differentiate output 
                     addresses.                                          
-v [--version]       The transaction version, defaults to 1.
```
See also [tx-decode](bx-tx-decode).
### Example 1
one input, payment address output
```sh
$ bx tx-encode -i 97e06e49dfdd26c5a904670971ccf4c7fe7d9da53cb379bf9b442fc9427080b3:0 -o 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb:45000
```
```
0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
### Example 2
one input, stealth address output
```sh
$ bx tx-encode -i 97e06e49dfdd26c5a904670971ccf4c7fe7d9da53cb379bf9b442fc9427080b3:0 -o hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i:42:baadf00dbaadf00dbaadf00dbaadf00d
```
```
0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970000000000ffffffff0200000000000000003a6a3814576f496f20b0befe21f39f765e81543ebd1790ec4a03d1b5a1c2e912749d90d0fd7b16322749e301a2b0dbfe27850901156459000000002a000000000000001976a914cc04492c12d0ddeb4cf88cfccb0d6d78d0fcd39d88ac00000000
```
### Example 3
one input with index 1 and sequence 7, script output
```sh
$ bx tx-encode -i 97e06e49dfdd26c5a904670971ccf4c7fe7d9da53cb379bf9b442fc9427080b3:1:7 -o 76a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac:500
```
```
0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee09701000000000700000001f4010000000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000
```