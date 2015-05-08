Convert a mnemonic seed (BIP39) to its numeric representation.
```sh
$ bx mnemonic-to-seed --help
```
```
Usage: bx mnemonic-to-seed [-h] [--config VALUE] [--language VALUE]      
[--passphrase VALUE] [WORD]...                                           

Info: Convert a mnemonic seed (BIP39) to its numeric representation.     

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-l [--language]      The language identifier of the dictionary of the    
                     mnemonic. Options are 'en', 'es', 'ja', 'zh_Hans',  
                     'zh_Hant' and 'any', defaults to 'any'.             
-p [--passphrase]    An optional passphrase for converting the mnemonic  
                     to a seed.                                          

Arguments (positional):

WORD                 The set of words that that make up the mnemonic. If 
                     not specified the words are read from STDIN.
```
See also [mnemonic-new](bx-mnemonic-new).
### Example 1
```sh
$ bx mnemonic-to-seed rival hurdle address inspire tenant almost turkey safe asset step lab boy
```
```
020b67fd929e0eb9f963443138057ceec0d62601d69b4b2327c00d74f0fd1862d164c53d49227d9dadedbbec305236bc2149d9a5267aa7c5aa004235c3c66c29
```
### Example 2
invalid dictionary
```sh
$ bx mnemonic-to-seed --language ja rival hurdle address inspire tenant almost turkey safe asset step lab boy
```
```
The specified words are not a valid mnemonic in the specified dictionary.
```