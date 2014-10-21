Derive the stealth public key necessary to address and to identify a stealth payment.
```sh
$ bx stealth-public --help
```
```
Usage: bx stealth-public [-h] [--config VALUE] SPEND_PUBKEY              
[SHARED_SECRET]                                                          

Info: Derive the stealth public key necessary to identify a stealth      
payment.                                                                 

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SPEND_PUBKEY         The Base16 EC spend public key of a stealth address.
SHARED_SECRET        The Base16 EC shared secret corresponding to the    
                     SPEND_PUBKEY. If not specified the key is read from 
                     STDIN.
```
The **stealth public key** is independently derivable by the owner of the **ephemeral secret** (payer) and by the owner of the **scan secret** (receiver). In other words, any party that can obtain the **shared secret**. The stealth public key is used by the payer to generate the payment address and by the receiver to identify the payment.
### Example 1
spend public key, shared secret
```sh
$ bx stealth-public 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969 78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590
```
```
03ac9e60013853128b42a1324609bac2ccff6a0b4844b6301f1f552e15ee14c7a5
```
### Example 2
piped commands, ephemeral secret and scan public key
```sh
$ bx stealth-shared 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 | bx stealth-public 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590
03ac9e60013853128b42a1324609bac2ccff6a0b4844b6301f1f552e15ee14c7a5
```

> Notice that the three EC values necessary to generate the stealth public key can be combined in a single command line.

### Example 3
piped commands, scan secret and ephemeral public key
```sh
$ bx stealth-shared af4afaeb40810e5f8abdbb177c31a2d310913f91cf556f5350bca10cbfe8b9ec 0247140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36 | bx stealth-public 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590
03ac9e60013853128b42a1324609bac2ccff6a0b4844b6301f1f552e15ee14c7a5
```

> This is a non-typical scenario as the user holds both the ephemeral secret and the scan secret. This implies that the user is operating in the role of payer and receiver.