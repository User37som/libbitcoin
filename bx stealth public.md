Derive the stealth public key necessary to identify a stealth payment.
```sh
$ bx stealth-public [-h] [--config VALUE] EPHEMERAL_PUBKEY SCAN_SECRET   
SPEND_PUBKEY                                                             
```
```
Info: Derive the stealth public key necessary to identify a stealth      
payment.                                                                 

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

EPHEMERAL_PUBKEY     The Base16 ephemeral EC public key retrieved from   
                     the stealth payment metadata.                       
SCAN_SECRET          The Base16 EC private key corresponding to the      
                     public key required to generate a stealth payment.  
SPEND_PUBKEY         A Base16 EC public key corresponding to a private   
                     key that can spend payments to the stealth address.
```
### Example 1
```sh
$ 
```
```
```