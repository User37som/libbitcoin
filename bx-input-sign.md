Create a signature for a transaction input.
```sh
$ bx input-sign --help
```
```
Usage: bx input-sign [-h] [--config VALUE] [--index VALUE] [--sign_type  
VALUE] EC_PRIVATE_KEY NONCE PREVOUT_SCRIPT TRANSACTION                   

Info: Create a signature for a transaction input.                        

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-i [--index]         The ordinal position of the input within the        
                     transaction, defaults to zero.                      
-s [--sign_type]     A token that indicates how the transaction should be
                     hashed for signing. Options are 'all', 'none',      
                     'single', and 'anyone_can_pay', defaults to         
                     'single'.                                           

Arguments (positional):

EC_PRIVATE_KEY       The Base16 EC private key to sign with.             
NONCE                The Base16 random value to be used as the signing   
                     nonce. Must be at least 128 bits in length.         
PREVOUT_SCRIPT       The previous output script to use in signing.       
TRANSACTION          The Base16 transaction. If not specified the        
                     transaction is read from STDIN.
```
### Example 1
```sh
$ 
```
```
```