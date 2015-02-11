Encode an unsigned transaction as Base16.
```sh
$ bx tx-encode --help
```
```
Usage: bx tx-encode [-h] [--config VALUE] [--input VALUE] [--lock_time   
VALUE] [--output VALUE] [--version VALUE]               

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
                     SATOSHI is the 32 bit spend amount in satoshi. SEED 
                     is required for stealth outputs and not used        
                     otherwise. The same seed should NOT be used for     
                     multiple outputs.                                   
-v [--version]       The transaction version.                            
```
See also [tx-decode](bx-tx-decode).
### Example 1
one input, one output
```sh
$ bx tx-encode -i 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d:0 -o 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb:45000
```
```
01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c0000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```