Create a new stealth public key from which a payment address can be generated.
```sh
$ bx stealth-new --help
```
```
Usage: bx stealth-new [-h] [--config VALUE] EPHEMERAL_SECRET SCAN_PUBKEY 
SPEND_PUBKEY                                                             

Info: Create a new stealth public key from which a payment address can be
generated.                                                               

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

EPHEMERAL_SECRET     The Base16 ephemeral EC private key used to generate
                     stealth payment metadata. A unique value should be  
                     used for each stealth payment.                      
SCAN_PUBKEY          The Base16 EC public key required to generate a     
                     stealth address.                                    
SPEND_PUBKEY         A Base16 EC public key corresponding to a private   
                     key that can spend payments to the stealth address.
```
This command is used by a payer to generate a new public key, from which a payment address may be derived, to which the payment may be made.
### Example 1
```sh
$ 
```
```
```