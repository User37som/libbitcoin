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
invalid mnemonic
```sh
$ bx mnemonic-to-seed two words
```
```
The number of words must be divisible by 3.
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
$ bx mnemonic-to-seed 值 所 毕 没 流 妨 性 守 解 芯 威 隔
```
```
46d1593a3b78c9c557aa956e767836f97552486ac233dd6cd8d874d95a127890b7d560509bdba0468227f41e42c730b36c38fd3428cdecf841b64ecd17dc48d6
```
### Example 7
Traditional Chinese
```sh
$ bx mnemonic-to-seed 值 所 畢 沒 流 妨 性 守 解 芯 威 隔
```
```
73c4cc1c492ba13285093e774a2785078d4545e3c4d519ddb46efbf991f7a89c7aa65739eb5b91df8f92838530f544ed0eede0fda06f6f1876ce5be403bed3b1
```
### Example 8
--passphrase
```sh
$ bx mnemonic-to-seed 值 所 畢 沒 流 妨 性 守 解 芯 威 隔 --passphrase "one point twenty-one gigawats"
```
```
aef417acfb9457f60b797575ce76540c944e489294b7acb4125f1244ecdf9c00d2f5b160a5c26e786739cd35ec1448eb5d870640d36feb63d3570793b627472d
```
### Example 9
unknown dictionary
```sh
$ bx mnemonic-to-seed 值 所 畢 hurdle address inspire tenant ねんかん すずしい pulpo anís señal
```
```
WARNING: The specified words are not a valid mnemonic in any supported dictionary.
8a377e0eee9b64371ca3554d787fe3d2045869dd4e31012beeafeb69ed11a866214cf776213f06b8398bc1567ce3294fb8eac7942da21c1f84eae8729a20ef23
```
### Example 10
piped commands
```sh
$ bx seed | bx mnemonic-new | bx mnemonic-to-seed | bx hd-new
```
```
655a1ed2d4fef69bb314198c7327f23c
grab special regret prepare urge evidence slush lobster midnight odor wish ketchup
57bae342ae8e69eb63f17ef993a90a59159e0f78114b602bf0ebabfec0e5d086e883c31975bf03f8a47a32853452623094d1303fd0549745db457145e5756582
xprv9s21ZrQH143K43CUCgNp5SmXzg2axQx2P4WupA2zEnKpFM19QfqfdqfpJR3yfzAXZnsHeUaQhWQMwyuqL8DbdeLeCbdMoKNn6pCY4RUn2pK
```