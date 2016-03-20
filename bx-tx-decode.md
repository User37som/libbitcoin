Decode a Base16 transaction.
```sh
$ bx tx-decode --help
```
```
Usage: bx tx-decode [-h] [--config VALUE] [--format VALUE] [TRANSACTION] 

Info: Decode a Base16 transaction.                                       

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

TRANSACTION          The Base16 transaction. If not specified the        
                     transaction is read from STDIN.
```
See also [tx-encode](bx-tx-encode).
### Example 1
unsigned, one input, payment address output
```sh
$ bx tx-decode 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee0970000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```js
transaction
{
    hash f9be6abf60342de5606421c7deaaf2d3f7133490db5242e8507e05926b16d090
    inputs
    {
        input
        {
            previous_output
            {
                hash 97e06e49dfdd26c5a904670971ccf4c7fe7d9da53cb379bf9b442fc9427080b3
                index 0
            }
            script ""
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb
            script "dup hash160 [ 58b7a60f11a904feef35a639b6048de8dd4d9f1c ] equalverify checksig"
            value 45000
        }
    }
    version 1
}
```
### Example 2
unsigned, one input, stealth address output
```sh
$ bx tx-decode 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee09701000000000700000001f4010000000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000
```
```js
transaction
{
    hash eaa1fa9c373a56ab0bf4697075f2d2fc5cc61351b183173d097e44ead82c60ed
    inputs
    {
        input
        {
            previous_output
            {
                hash 97e06e49dfdd26c5a904670971ccf4c7fe7d9da53cb379bf9b442fc9427080b3
                index 0
            }
            script ""
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            script "return [ 14576f496f20b0befe21f39f765e81543ebd1790ec4a03d1b5a1c2e912749d90d0fd7b16322749e301a2b0dbfe2785090115645900000000 ]"
            stealth
            {
                prefix 3146755417
                ephemeral_public_key 0214576f496f20b0befe21f39f765e81543ebd1790ec4a03d1b5a1c2e912749d90
            }
            value 0
        }
        output
        {
            address 1KbjyvFBRc2p6dKpTfDAFdT5DqmVLGX3B4
            script "dup hash160 [ cc04492c12d0ddeb4cf88cfccb0d6d78d0fcd39d ] equalverify checksig"
            value 42
        }
    }
    version 1
}
```
### Example 3
unsigned, one input with index 1 and sequence 7, script output
```sh
$ bx tx-decode 0100000001b3807042c92f449bbf79b33ca59d7dfec7f4cc71096704a9c526dddf496ee09701000000000700000001f4010000000000001976a91418c0bd8d1818f1bf99cb1df2269c645318ef7b7388ac00000000
```
```js
transaction
{
    hash bfe73280b111a7dae1714b1efe869c0d0c854dd9d1c3ba51fa439e7fb4d0e63c
    inputs
    {
        input
        {
            previous_output
            {
                hash 97e06e49dfdd26c5a904670971ccf4c7fe7d9da53cb379bf9b442fc9427080b3
                index 1
            }
            script ""
            sequence 7
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe
            script "dup hash160 [ 18c0bd8d1818f1bf99cb1df2269c645318ef7b73 ] equalverify checksig"
            value 500
        }
    }
    version 1
}
```
### Example 4
signed transaction
```sh
$ bx tx-decode 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c000000006b4830450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af68174012103e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```js
transaction
{
    hash 37c9c4ee0e84c7c7924f74d92cf0779ec6e8fc4c57ebab2593562d52c61c5eb8
    inputs
    {
        input
        {
            address 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
            previous_output
            {
                hash 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
                index 0
            }
            script "[ 30450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af6817401 ] [ 03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31 ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb
            script "dup hash160 [ 58b7a60f11a904feef35a639b6048de8dd4d9f1c ] equalverify checksig"
            value 45000
        }
    }
    version 1
}
```