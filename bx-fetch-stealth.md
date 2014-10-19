Get metadata on potential payment transactions by stealth prefix.
```sh
$ bx fetch-stealth --help
```
```
Usage: bx fetch-stealth [-h] [--config VALUE] [--format VALUE] [--height 
VALUE] [PREFIX]                                                          

Info: Get metadata on potential payment transactions by stealth prefix.  
Requires an Obelisk server connection.                                   

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'json', 'xml', 'info'
                     or 'native', defaults to native.                    
-h [--help]          Get a description and instructions for this command.
-t [--height]        The minimum block height of transactions to include.

Arguments (positional):

PREFIX               The Base2 stealth prefix used to locate             
                     transactions. Defaults to all stealth transactions.
```
The number of transactions matching a given prefix will increase over time.
### Example 1
```sh
$ bx fetch-stealth 101010
```
```js
stealth
{
    match
    {
        ephemeral_public_key 03c35235b93427c39f477a83c493d2ea74d9195dc8a3b3e7dbb5ad88584b1472d2
        paid_address 1C8cs6vuuHqN7dtHqh13Yc6395unYcpSC6
        transaction_hash d216cd6596d4119acba1b8d786cdeb15f76f01d8a3ee12603e2581950857b736
    }
    match
    {
        ephemeral_public_key 037d2dc47d2cdef67eb84996b9df9d91d66624651d4902b82b1655f884f871328d
        paid_address 1EokigXmAJsZarQ7v36BYxeSy16gAAvZW4
        transaction_hash d3bff487e6b74141653035f6318545b129ca519ee0fecb616cdf764899ad23ff
    }
    match
    {
        ephemeral_public_key 0307d4526afaa699eec1d4b53570d08f56d12f825079ffeda9f6f41aa6fc943613
        paid_address 13LVHNKKc3kZrFF28foBY4pXwovMiZQ6gY
        transaction_hash 0406227a7d441e776d67d723da08a2d0e39714d0eb07d927cbf45dee8a2a23b9
    }
    match
    {
        ephemeral_public_key 03a386356c978169f1af8c69c8aa6ae5932c27919f5ebb6e9f05d728df6913f700
        paid_address 14ZrpgUDPuAsVXcei35MRFTv6oCYmPc1uV
        transaction_hash 2b0580d7aaf27a231a3905d45c332ba2c17bef343304d7486429b6e5b14c0294
    }
}
```
### Example 2
--height 325500, prefix 10
```sh
$ bx fetch-stealth -t 325500 10
```
```js
stealth
{
    match
    {
        ephemeral_public_key 032f75f66b02edcdafa6256c6df4fc88a8888affaffe25593dfd2bdd8d21b34ff3
        paid_address 1DzpwUdSBrpUbSUfgePxw7x6n3TSttE6is
        transaction_hash 40c0d8d3de7b89ef8d1b8d91884755c3008e998e8e4095001e3cf3fd5c920dbc
    }
    match
    {
        ephemeral_public_key 02e9b470d57eb92bfcb36bdf27413e815767b5f2a9c2f267c7b1fcf103a0e388a5
        paid_address 1KcApvGbZRbzEeZ2MurUy4FtanPYJTCwmX
        transaction_hash b17124b2058a601682ece0dd6471abe631f0e3d93a10f141004bd49225b30610
    }
    match
    {
        ephemeral_public_key 02bb0e46079aaf456a03a415ddf12c18f1c2fb72d444c149b982d14d3961976f75
        paid_address 19vL1achobaddRxbSy28sQ4mKSVKpPXUiR
        transaction_hash c55eaacff0abd23e339f299a12f302379626ed75917d1b5da98186e9c20add45
    }
    match
    {
        ephemeral_public_key 030fc8adeced0bdafb77a986c46941f189048a31a36e75f92817e702011a4024f1
        paid_address 1EARiXX6XY3CGbCN9T3M72o5sPGCfWnerM
        transaction_hash a0ef776d8a136b1de8515a15164cd3433a657caa31c42c02b61b4b735fce8ffb
    }
}
```
### Example 3
pipe to file, all stealth transactions 
```sh
$ bx fetch-stealth -f xml > stealth.xml
```