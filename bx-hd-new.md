Create a new HD (BIP32) private key from entropy.   
```sh
```
$ bx hd-new --help
```
Usage: bx hd-new [-h] [--config VALUE] [SEED]                            

Info: Create a new HD (BIP32) private key from entropy.                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SEED                 The Base16 randomness seed for the new key. Must be 
                     at least 128 bits in length. If not specified the   
                     seed is read from STDIN.  
```
### Example 1
```
$ bx hd-new baadf00dbaadf00dbaadf00dbaadf00d
```
```
xprv9s21ZrQH143K3bJ7oEuyFtvSpSHmdsmfiPcDXX2RpArAvnuBwcUo8KbeNXLvdbBPgjeFdEpQCAuxLaAP3bJRiiTdw1Kx4chf9zSGp95KBBR
```