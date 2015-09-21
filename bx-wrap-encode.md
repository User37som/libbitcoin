Add a version byte and checksum to Base16 data.
```sh
$ bx wrap-encode --help
```
```
Usage: bx wrap-encode [-h] [--config VALUE] [--version VALUE] [PAYLOAD]  

Info: Add a version byte and checksum to Base16 data.                    

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-v [--version]       The desired version number.                         

Arguments (positional):

PAYLOAD              The Base16 data to wrap. If not specified the value 
                     is read from STDIN.
```
See also [wrap-decode](bx-wrap-decode).
### Example 1
--version 0
```sh
$ bx wrap-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
00031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd0065b09d03c
```
### Example 2 
--version 158 ([DOGE](https://github.com/libbitcoin/libbitcoin/wiki/BIP44-Altcoin-Version-Mappings#bip44-altcoin-version-mapping-table) version/WIF column)

*Result below is the same as a DOGE "base58check-encode" of a EC private key.*
```sh
$ bx wrap-encode -v 158 1f59dd4ea6629da7970ca374513dd0061bab84e687e36514eeaf5a017c30d32c | bx base58-encode
```
```
9e1f59dd4ea6629da7970ca374513dd0061bab84e687e36514eeaf5a017c30d32cdf35712f
6JNRhCcL62kb5oKbU7Ur61QxVngwntjNAgL1Ni1owZtkUfEoNFG
```
### Example 3
Demonstrate `wrap-encode` equivalence to steps 4-8 in *[Technical background of version 1 Bitcoin addresses]((https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses))*.
```sh
$ bx wrap-encode 010966776006953d5567439e5e39f86a0d273bee | bx base58-encode
```
```
00010966776006953d5567439e5e39f86a0d273beed61967f6
16UwLL9Risc3QfPqBUvKofHmBQ7wMtjvM
```
### Example 4
piped input
```sh
$ bx base16-encode "Satoshi Nakamoto" | bx wrap-encode
```
```
5361746f736869204e616b616d6f746f
005361746f736869204e616b616d6f746f5311991f
```

### Example 5
--version 30 ([DOGE](https://github.com/libbitcoin/libbitcoin/wiki/BIP44-Altcoin-Version-Mappings#bip44-altcoin-version-mapping-table) version/p2pkh column)

*Computes a DOGE address by using wrap-encode piped to base58-encode. Result below complements example #3. *

```sh
$ bx ec-to-public 1f59dd4ea6629da7970ca374513dd0061bab84e687e36514eeaf5a017c30d32c | bx sha256 | bx ripemd160 | bx wrap-encode -v 30 | bx base58-encode
```
```
03eb43e9bc959fae807c24d5907b35f0e680d340064a26e1b15f14d466f6c87c2c
10501126cf0bfe0ccb4165453fdd46b25ca2d0a6845a3e822a223f9aa8f259a4
75ac7c0d9b0871fe1cec13a33b99039b01ffd8f4
1e75ac7c0d9b0871fe1cec13a33b99039b01ffd8f44ce5c709
DFsJE9AFsHmmtaxHBS9ETr2esJuMSAevMN
```