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
### Example 1
--version 0
```sh
$ bx wrap-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
00031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd0065b09d03c
```
### Example 2
--version 42
```sh
$ bx wrap-encode -v 42 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
2a031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006298eebe4
```
### Example 3
*[Technical background of version 1 Bitcoin addresses]((https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses))*

0 - Having a private ECDSA key
```
18e14a7b6a307f426a94f8114701e7c8e774e7f9a47e2c2035db29a206321725
```
1 - Take the corresponding public key generated with it (65 bytes, 1 byte 0x04, 32 bytes corresponding to X coordinate, 32 bytes corresponding to Y coordinate)
```sh
$ bx ec-to-public -u 18e14a7b6a307f426a94f8114701e7c8e774e7f9a47e2c2035db29a206321725
```
```
0450863ad64a87ae8a2fe83c1af1a8403cb53f53e486d8511dad8a04887e5b23522cd470243453a299fa9e77237716103abc11a1df38855ed6f2ee187e9c582ba6
```
2 - Perform SHA-256 hashing on the public key
```sh
$ bx sha256 0450863ad64a87ae8a2fe83c1af1a8403cb53f53e486d8511dad8a04887e5b23522cd470243453a299fa9e77237716103abc11a1df38855ed6f2ee187e9c582ba6
```
```
600ffe422b4e00731a59557a5cca46cc183944191006324a447bdb2d98d4b408
```
3 - Perform RIPEMD-160 hashing on the result of SHA-256
```sh
$ bx ripemd160 600ffe422b4e00731a59557a5cca46cc183944191006324a447bdb2d98d4b408
```
```
010966776006953d5567439e5e39f86a0d273bee
```
4 - Add version byte in front of RIPEMD-160 hash (0x00 for Main Network)
```
00010966776006953d5567439e5e39f86a0d273bee
```
5 - Perform SHA-256 hash on the extended RIPEMD-160 result
```sh
$ bx sha256 00010966776006953d5567439e5e39f86a0d273bee
```
```
445c7a8007a93d8733188288bb320a8fe2debd2ae1b47f0f50bc10bae845c094
```
6 - Perform SHA-256 hash on the result of the previous SHA-256 hash
```sh
$ bx sha256 445c7a8007a93d8733188288bb320a8fe2debd2ae1b47f0f50bc10bae845c094
```
```
d61967f63c7dd183914a4ae452c9f6ad5d462ce3d277798075b107615c1a8a30
```
7 - Take the first 4 bytes of the second SHA-256 hash. This is the address checksum
```
d61967f6
```
8 - Add the 4 checksum bytes from stage 7 at the end of extended RIPEMD-160 hash from stage 4. This is the 25-byte binary Bitcoin Address.
```
00010966776006953d5567439e5e39f86a0d273beed61967f6
```
9 - Convert the result from a byte string into a base58 string using Base58Check encoding. This is the most commonly used Bitcoin Address format
```sh
$ bx base58-encode 00010966776006953d5567439e5e39f86a0d273beed61967f6
```
```
16UwLL9Risc3QfPqBUvKofHmBQ7wMtjvM
```
### Example 4
Show equivalence to steps 4-8 in Example 2.
```sh
$ bx wrap-encode 010966776006953d5567439e5e39f86a0d273bee | bx base58-encode
```
```
00010966776006953d5567439e5e39f86a0d273beed61967f6
16UwLL9Risc3QfPqBUvKofHmBQ7wMtjvM
```