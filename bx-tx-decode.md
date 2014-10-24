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
```sh
$ bx tx-decode 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c0000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```js
transaction
{
    hash e433a95114dc4eb2209f7c329bad265890affb728a60ac1b967d99bbe1f25971
    inputs
    {
        input
        {
            previous_output
            {
                hash 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
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