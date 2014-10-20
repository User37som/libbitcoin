Validate a transaction signature.
```sh
$ bx input-validate --help
```
```
Usage: bx input-validate [-h] [--config VALUE] [--index VALUE]           
[--sign_type VALUE] EC_PUBLIC_KEY PREVOUT_SCRIPT SIGNATURE TRANSACTION   

Info: Validate a transaction signature.                                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-i [--index]         The ordinal position of the input within the        
                     transaction, defaults to zero.                      
-s [--sign_type]     A token that indicates how the transaction was      
                     hashed for signing. Options are 'all', 'none',      
                     'single', and 'anyone_can_pay', defaults to         
                     'single'.                                           

Arguments (positional):

EC_PUBLIC_KEY        The Base16 EC public key to verify against.         
PREVOUT_SCRIPT       The previous output script used in signing.         
SIGNATURE            The Base16 signature to validate.                   
TRANSACTION          The Base16 transaction. If not specified the        
                     transaction is read from STDIN.
```
### Example 1
```sh
$ 
```
```
```