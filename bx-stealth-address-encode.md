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
scan key only
```sh
$ bx stealth-address-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
```
### Example 2
scan key and redundant spend key
```sh
$ bx stealth-address-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
```

> Notice that the stealth address remains unchanged when the spend key is explicitly the same as the scan key.

### Example 3
scan key and one different spend key
```sh
$ bx stealth-address-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
vJmwY32eS5VDC2C4GaZyXt7i4iCjzSMZ1XSd6KbkA7QbGE492akT2eZZMjCwWDqKRSYhnSA8Bgp78KeAYFVCi8ke5mELdoYMBNep7L
```