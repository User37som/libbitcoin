Derive the stealth private key necessary to spend a stealth payment.
```sh
$ bx stealth-secret --help
```
```
Usage: bx stealth-secret [-h] [--config VALUE] SPEND_SECRET              
[SHARED_SECRET]                                                          

Info: Derive the stealth private key necessary to spend a stealth        
payment.                                                                 

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SPEND_SECRET         The Base16 EC spend secret for spending a stealth   
                     payment.                                            
SHARED_SECRET        The Base16 EC shared secret corresponding to the    
                     SPEND_PUBKEY. If not specified the key is read from 
                     STDIN.
```
### Example 1
spend secret, shared secret (parameters reversed)
```sh
$ bx stealth-secret d39758028e201e8edf6d6eec6910ae4038f9b1db3f2d4e2d109ed833be94a026 78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590
```
```
4c721ccd679b817ea5e86e34f9d46abb1660a63955dde908702214eaab038475
```
### Example 2
shared secret, spend secret
```sh
$ bx stealth-secret 78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590 d39758028e201e8edf6d6eec6910ae4038f9b1db3f2d4e2d109ed833be94a026
```
```
4c721ccd679b817ea5e86e34f9d46abb1660a63955dde908702214eaab038475
```

> Notice that the order of the parameters is not consequential.