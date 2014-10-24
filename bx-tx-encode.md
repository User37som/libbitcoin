Encode an unsigned transaction as Base16.
```sh
$ bx tx-encode --help
```
```
Usage: bx tx-encode [-h] [--config VALUE] [--input VALUE] [--lock_time   
VALUE] [--output VALUE] [--version VALUE] [TRANSACTION]                  

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

Arguments (positional):

TRANSACTION          The encoded transaction file path. If not specified 
                     the transaction is written to STDOUT.
```
See also [tx-decode](bx-tx-decode).
### Example 1
```
$ 
```
```
```