Create a mnemonic seed (BIP39) from entropy.
```sh
$ bx mnemonic-new --help
```
```
Usage: bx mnemonic-new [-h] [--config value] [--language value] [SEED]

Info: Create a mnemonic seed (BIP39) from entropy. WARNING: mnemonic
should be created from properly generated entropy.

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this command.
-l [--language]      The language identifier of the mnemonic dictionary
                     to use. Options are 'en', 'es', 'fr', 'it', 'ja',
                     'zh_Hans', 'zh_Hant' and 'any', defaults to 'en'.

Arguments (positional):

SEED                 The Base16 entropy from which the mnemonic is
                     created. The length must be evenly divisible by 32
                     bits. If not specified the entropy is read from
                     STDIN.
```
See also [mnemonic-to-seed](bx-mnemonic-to-seed).
### Example 1
invalid seed
```sh
$ bx mnemonic-new baad
```
```
The seed length in bytes is not evenly divisible by 32 bits.
```
### Example 2
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d
```
```
rival hurdle address inspire tenant almost turkey safe asset step lab boy
```
### Example 3
piped commands, 128 bit seed
```sh
$ bx seed -b 128 | bx mnemonic-new
```
```
36e0ee880a21b1fe4333121499f5d0c9
dad alter pear begin brand you art girl behind soul injury napkin
```
### Example 4
--language es
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d --language es
```
```
previo humilde actuar jarabe tabique ahorro tope pulpo anís señal lavar bahía
```
### Example 5
--language fr
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d --language fr
```
```
placard garantir acerbe gratuit soluble affaire théorie ponctuel anguleux salon horrible bateau
```
### Example 6
--language it
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d --language it
```
```
rizoma lastra affabile lucidato sultano algebra tramonto rupe annuncio sonda mega bavosa
```
### Example 7
--language ja
```sh
$ bx mnemonic-new baadf00dbaadf00dbaadf00dbaadf00d --language ja
```
```
ねんかん すずしい あひる せたけ ほとんど あんまり めいあん のべる いなか ふとる ぜんりゃく えいせい
```
### Example 8
--language zh_Hans
```sh
$ bx mnemonic-new 36e0ee880a21b1fe4333121499f5d0c9 -l zh_Hans
```
```
值 所 毕 没 流 妨 性 守 解 芯 威 隔
```
### Example 9
--language zh_Hant
```sh
$ bx mnemonic-new 36e0ee880a21b1fe4333121499f5d0c9 -l zh_Hant
```
```
值 所 畢 沒 流 妨 性 守 解 芯 威 隔
```