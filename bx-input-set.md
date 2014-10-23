Assign a script to an existing transaction input.
```sh
$ bx input-set --help
```
```
Usage: bx input-set [-h] [--config VALUE] [--index VALUE]                
SIGNATURE_SCRIPT [TRANSACTION]                                           

Info: Assign a script to an existing transaction input.                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-i [--index]         The ordinal position of the input within the        
                     transaction, defaults to zero.                      

Arguments (positional):

SIGNATURE_SCRIPT     The signature script to assign to the input.        
TRANSACTION          The Base16 transaction. If not specified the        
                     transaction is read from STDIN.
```
### Example 1
assign a signature script to the first transaction input, index 0

For the [previous step](bx-input-sign#example-1) see Example 1 of the `input-sign` command.

The private key, signature, and transaction are carried over from the previous step.

Derive the **public key** corresponding to the private key.
```sh
$ bx ec-to-public 4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350
```
```
03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31
```
Create a **signature script** using the signature and public key, and assign it to the first input of the transaction. The result is an updated version of the original transaction.
```sh
$ bx input-set "[ 30450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af6817401 ] [ 03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31 ]" 01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c0000000000ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
```
01000000017d01943c40b7f3d8a00a2d62fa1d560bf739a2368c180615b0a7937c0e883e7c000000006b4830450221008f66d188c664a8088893ea4ddd9689024ea5593877753ecc1e9051ed58c15168022037109f0d06e6068b7447966f751de8474641ad2b15ec37f4a9d159b02af68174012103e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31ffffffff01c8af0000000000001976a91458b7a60f11a904feef35a639b6048de8dd4d9f1c88ac00000000
```
For the [next step](bx-input-validate#example-1) see Example 1 of the `input-validate` command.

The **complete scenario** is detailed in [How to Receive and Spend](How-to-Receive-and-Spend).