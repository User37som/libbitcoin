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
### Example 1
```sh
$ 
```
```
```