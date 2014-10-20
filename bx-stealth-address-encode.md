Encode a stealth payment address. 
```sh
$ bx stealth-address-encode --help
```
```
Usage: bx stealth-address-encode [-h] [--config VALUE] [--prefix VALUE]  
[--signatures VALUE] SCAN_PUBKEY [SPEND_PUBKEY]...                       

Info: Encode a stealth payment address.                                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-p [--prefix]        The Base2 stealth prefix that will be used to locate
                     payments.                                           
-s [--signatures]    Specify the number of signatures required to spend a
                     payment to the stealth address. Defaults to the     
                     number of SPEND_PUBKEYs.                            

Arguments (positional):

SCAN_PUBKEY          The Base16 EC public key required to generate a     
                     payment.                                            
SPEND_PUBKEY         The set of Base16 EC public keys corresponding to   
                     private keys that will be able to spend payments to 
                     the address. Defaults to the value of               
                     SCAN_EC_PUBLIC_KEY.
```
### Example 1
```sh
```
```
```