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
See also [mnemonic-to-seed](bx-mnemonic-to-seed).
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
### Example 3
--language es
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d --language es
```
```
previo humilde actuar jarabe tabique ahorro tope pulpo anís señal lavar bahía
```
### Example 4
--language ja
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d --language ja
```
```
ねんかん すずしい あひる せたけ ほとんど あんまり めいあん のべる いなか ふとる ぜんりゃく えいせい
```
### Example 5
--language zh_Hans
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d --language zh_Hans
```
```
博 肉 地 危 惜 多 陪 荒 因 患 伊 基
```
### Example 6
--language zh_Hant
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d --language zh_Hant
```
```
博 肉 地 危 惜 多 陪 荒 因 患 伊 基
```