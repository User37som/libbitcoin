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
any dictionary
```sh
$ bx mnemonic-to-seed rival hurdle address inspire tenant almost turkey safe asset step lab boy
```
```
020b67fd929e0eb9f963443138057ceec0d62601d69b4b2327c00d74f0fd1862d164c53d49227d9dadedbbec305236bc2149d9a5267aa7c5aa004235c3c66c29
```
### Example 2
incorrect specified dictionary
```sh
$ bx mnemonic-to-seed --language ja rival hurdle address inspire tenant almost turkey safe asset step lab boy
```
```
The specified words are not a valid mnemonic in the specified dictionary.
`````
### Example 3
correct specified dictionary
```sh
$ bx mnemonic-to-seed --language en rival hurdle address inspire tenant almost turkey safe asset step lab boy
```
```
020b67fd929e0eb9f963443138057ceec0d62601d69b4b2327c00d74f0fd1862d164c53d49227d9dadedbbec305236bc2149d9a5267aa7c5aa004235c3c66c29
```
### Example 4
Spanish
```sh
$ bx mnemonic-to-seed previo humilde actuar jarabe tabique ahorro tope pulpo anís señal lavar bahía
```
```
9cc236d5fa28c39e835bd6f7d66b51056c3a2f56208da1c1c2997a3741fe60bb0645d849ecacff0a29f2e26977ae42b12b97a5a3a8cc78d7113b536ff069352e
```
### Example 5
Japanese
```sh
$ bx mnemonic-to-seed ねんかん すずしい あひる せたけ ほとんど あんまり めいあん のべる いなか ふとる ぜんりゃく えいせい
```
```
7080e13e2e306aa2f92b56c0a2d66de62c616c4d5a3bee9c026c37172c93e4aac47d6a16c9ddc28132f5a037862c0cfc747e6f272f55016ddbf8b8206d331237
```
### Example 6
Simplified Chinese
```sh
$ bx mnemonic-to-seed 博 肉 地 危 惜 多 陪 荒 因 患 伊 基
```
```
a7d6aa4f8e23bb666ad8d5ee58df85824a93d69a306547433bd047173d45ddaf7595d98b00386af5b8ddfce2666792961cfa70bbe71b97cb211811a7512b8d2b
```
### Example 7
Traditional Chinese
```sh
$ bx mnemonic-to-seed 博 肉 地 危 惜 多 陪 荒 因 患 伊 基
```
```
a7d6aa4f8e23bb666ad8d5ee58df85824a93d69a306547433bd047173d45ddaf7595d98b00386af5b8ddfce2666792961cfa70bbe71b97cb211811a7512b8d2b
```