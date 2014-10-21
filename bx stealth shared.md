Derive the secret shared between an ephemeral key pair and a scan key pair.
```sh
$ bx stealth-shared --help
```
```
Usage: bx stealth-shared [-h] [--config VALUE] SECRET PUBKEY             

Info: Derive the secret shared between an ephemeral key pair and a scan  
key pair. Provide scan SECRET and ephemeral PUBKEY, or ephemeral SECRET  
and scan PUBKEY.                                                         

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SECRET               A Base16 EC private key. Either the scan or         
                     ephemeral secret.                                   
PUBKEY               A Base16 EC public key. Either the scan or ephemeral
                     public key. 
```
Through the public exchange of public keys two parties can obtain a shared secret. The secret is unlocked by each only through possession of the private key corresponding to the exchanged public key.

In stealth terminology the **scan** secret is created by the receiver and the **ephemeral** secret is created by the spender. The scan secret can be safely reused and the ephemeral secret should be unique for each payment. Each secret (or private key) has a derivable public key.
### Example 1
scan secret, ephemeral public key
```sh
$ bx stealth-shared af4afaeb40810e5f8abdbb177c31a2d310913f91cf556f5350bca10cbfe8b9ec 0247140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36
```
```
78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590
```
### Example 2
ephemeral secret, scan public key
```sh
$ bx stealth-shared 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
78dac4cad97b62efc67aff4890c3bc799815d144c5f93b171f559b43bca52590
```

> Notice the resulting shared secret is the same as in the previous example.