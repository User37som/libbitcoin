Validate a transaction input endorsement.
```sh
$ bx input-validate --help
```
```
Usage: bx input-validate [-h] [--config VALUE] [--index VALUE]           
EC_PUBLIC_KEY PREVOUT_SCRIPT ENDORSEMENT [TRANSACTION]                   

Info: Validate a transaction input endorsement.                          

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-i [--index]         The ordinal position of the input within the        
                     transaction, defaults to zero.                      

Arguments (positional):

EC_PUBLIC_KEY        The Base16 EC public key to verify against.         
PREVOUT_SCRIPT       The previous output script used in signing.         
ENDORSEMENT          The endorsement to validate.                        
TRANSACTION          The Base16 transaction. If not specified the        
                     transaction is read from STDIN.
```
### Example 1
validate the endorsement at the first transaction input, --index 0

For the [previous step](bx-input-set#example-1) see Example 1 of the `input-set` command.

The private key, previous output script, endorsement, and transaction are carried over from previous steps.
```sh
$ bx input-validate 03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31 "dup hash160 [ c564c740c6900b93afc9f1bdaef0a9d466adf6ee ] equalverify checksig" 30450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af6817401 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c000000006b4830450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af68174012103e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
The endorsement is valid.
```
The **complete scenario** is detailed in [How to Spend Bitcoin](How-to-Spend-Bitcoin).