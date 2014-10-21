Derive the stealth private key necessary to spend a stealth payment.
```sh
$ bx stealth-secret --help
```
```
Usage: bx stealth-secret [-h] [--config VALUE] EPHEMERAL_PUBKEY          
SCAN_SECRET SPEND_SECRET                                                 

Info: Derive the stealth private key necessary to spend a stealth        
payment.                                                                 

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

EPHEMERAL_PUBKEY     The Base16 ephemeral EC public key retrieved from   
                     the stealth payment metadata.                       
SCAN_SECRET          The Base16 EC private key corresponding to the      
                     public key required to generate a stealth address.  
SPEND_SECRET         A Base16 EC private key that can spend payments to  
                     the stealth address.
```
### Example 1
```sh
$ 
```
```
```