Create a mnemonic seed (BIP39) from entropy.
```sh
$ bx mnemonic-new --help
```
```
Usage: bx mnemonic-new [-h] [--config VALUE] [--language VALUE] [SEED]   

Info: Create a mnemonic seed (BIP39) from entropy. WARNING: mnemonic     
should be created from properly generated entropy.                       

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-l [--language]      The language identifier of the mnemonic dictionary  
                     to use. Options are 'en', 'es', 'ja', 'zh_Hans',    
                     'zh_Hant' and 'any', defaults to 'en'.              

Arguments (positional):

SEED                 The Base16 entropy from which the mnemonic is       
                     created. The length must be at least 128 bits and   
                     evenly divisible by 32 bits. If not specified the   
                     entropy is read from STDIN.
```
### Example 1
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d
```
```
rival hurdle address inspire tenant almost turkey safe asset step lab boy
```
### Example 2
piped commands
```sh
$ bx seed | bx mnemonic-new
```
```
36e0ee880a21b1fe4333121499f5d0c9
dad alter pear begin brand you art girl behind soul injury napkin
```