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

The **stealth secret** is knowable only to the owner of the **spend secret** (the receiver). With the spend secret and the shared secret the payment may be identified by the receiver and spent. It is necessary for the receiver to obtain the **ephemeral public key** for a given payment in order to derive the **shared secret**.

### Example 1
spend secret, shared secret
```sh
$ bx stealth-secret d39758028e201e8edf6d6eec6910ae4038f9b1db3f2d4e2d109ed833be94a026 78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590
```
```
4c721ccd679b817ea5e86e34f9d46abb1660a63955dde908702214eaab038475
```
### Example 2
piped commands, scan secret and ephemeral public key
```sh
$ bx stealth-shared af4afaeb40810e5f8abdbb177c31a2d310913f91cf556f5350bca10cbfe8b9ec 0247140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36 | bx stealth-secret d39758028e201e8edf6d6eec6910ae4038f9b1db3f2d4e2d109ed833be94a026
```
```
78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590
4c721ccd679b817ea5e86e34f9d46abb1660a63955dde908702214eaab038475
```

> Notice that the three EC values necessary to generate the stealth secret can be combined in a single command line.

### Example 3
piped commands, ephemeral secret and scan public key
```sh
$ bx stealth-shared 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 | bx stealth-secret  d39758028e201e8edf6d6eec6910ae4038f9b1db3f2d4e2d109ed833be94a026
```
```
78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590
4c721ccd679b817ea5e86e34f9d46abb1660a63955dde908702214eaab038475
```

> This is a non-typical scenario as the user holds both the ephemeral secret and the scan secret. This implies that the user is operating in the role of payer and receiver.

### Example 4
parameter reversal
```sh
$ bx stealth-secret 78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590 d39758028e201e8edf6d6eec6910ae4038f9b1db3f2d4e2d109ed833be94a026
```
```
4c721ccd679b817ea5e86e34f9d46abb1660a63955dde908702214eaab038475
```

> Notice that the order of the parameters is not consequential.