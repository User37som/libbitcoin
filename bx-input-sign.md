Create a signature for a transaction input.
```sh
$ bx input-sign --help
```
```
Usage: bx input-sign [-h] --nonce VALUE [--config VALUE] [--index VALUE] 
[--sign_type VALUE] EC_PRIVATE_KEY PREVOUT_SCRIPT [TRANSACTION]          

Info: Create a Bitcoin signature for a transaction input.                

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-i [--index]         The ordinal position of the input within the        
                     transaction, defaults to zero.                      
-n [--nonce]         The Base16 random value used to seed a signing      
                     nonce. Must be at least 128 bits in length.         
-s [--sign_type]     A token that indicates how the transaction should be
                     hashed for signing. Options are 'all', 'none',      
                     'single', and 'anyone_can_pay', defaults to 'all'.  

Arguments (positional):

EC_PRIVATE_KEY       The Base16 EC private key to sign with.             
PREVOUT_SCRIPT       The previous output script to use in signing.       
TRANSACTION          The Base16 transaction. If not specified the        
                     transaction is read from STDIN.
```
### Example 1
one input, one output, standard prevout script, sighash all

Start with one **input** point and one **output** point as follows.
```
--input 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d:0
--output 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb:45000
```
Create a random **nonce**.
```sh
$ bx seed
```
```
707e3d717925ba2e98234dd6f3a38eb5 
```

> In future versions the above step will be unnecessary and the `--nonce` parameter will be made optional.

Obtain the previous output **script** from the input point.
```sh
$ bx fetch-tx 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
```
```js
transaction
{
    hash 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d
    inputs
    {
        input
        {
            address 1PqLFcRyNMzsgcmT4Sd2XSVZ4XPb8CN8sj
            previous_output
            {
                hash df51c69f381a7511e95571382715cfd83c5384e9006ee7c546cfa6bb4b172346
                index 0
            }
            script "[ 304502206be979f1f89776e26abb40f458dc942d191d447cf3ce847d2d7e430df6b21ac4022100cade875670d71bd972f151b00544044d90a75261a9a01542968a1b36b31aea1801 ] [ 041fd7ca20852f638e82ac43b2df2ac7b38a3fec1622fb33c9f679ae909868a7e6e013429b2421a871a4e1d5d5702bea978bdd8ec399657dc6f3c0334a83de40bf ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
            script "dup hash160 [ c564c740c6900b93afc9f1bdaef0a9d466adf6ee ] equalverify checksig"
            value 100000
        }
        output
        {
            address 18kn866ztW2Y12DkijCubQmE6xBqmJS4Gr
            script "dup hash160 [ 55106ed6c650e125c28f767c83ccfbc0c231fc8a ] equalverify checksig"
            value 328860000
        }
    }
    version 1
}
```
The previous output script is at `transaction.outputs[0].script`.

> There are isolated cases where the script cannot be obtained literally from this location, however this is sufficient in more recent transactions. In cases where the script is of a typical form, as in this case, it may alternatively be inferred from the address.

The **private key** for the address `1JziqzXe...` of the previous output will be required for signing. The value is provided here for demonstration purposes.
```
4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350
```
Create a new **transaction**, using the input and output.
```sh
$ bx tx-encode -i 7c3e880e7c93a7b01506188c36a239f70b561dfa622d0aa0d8f3b7403c94017d:0 -o 1966U1pjj15tLxPXZ19U48c99EJDkdXeqb:45000
```
```
01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c0000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
Create a **signature** for the transaction, nonce, private key, previous output script and the transaction.
```sh
$ bx input-sign -n 707e3d717925ba2e98234dd6f3a38eb5 4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 "dup hash160 [ c564c740c6900b93afc9f1bdaef0a9d466adf6ee ] equalverify checksig" 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c0000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
30450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af6817401
```
For the **next step** see [Example 1](bx-input-set#example-1) of the `input-set` command.

The **complete scenario** is detailed in [How to Receive and Spend](How-to-Receive-and-Spend).