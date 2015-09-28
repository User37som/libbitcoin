This examples follows the article: [Technical background of version 1 Bitcoin addresses](https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses)

### Full Example

0 - Having a private ECDSA key.
```
18e14a7b6a307f426a94f8114701e7c8e774e7f9a47e2c2035db29a206321725
```
1 - Take the corresponding public key generated with it (65 bytes, 1 byte 0x04, 32 bytes corresponding to X coordinate, 32 bytes corresponding to Y coordinate).
```sh
$ bx ec-to-public -u 18e14a7b6a307f426a94f8114701e7c8e774e7f9a47e2c2035db29a206321725
```
```
0450863ad64a87ae8a2fe83c1af1a8403cb53f53e486d8511dad8a04887e5b23522cd470243453a299fa9e77237716103abc11a1df38855ed6f2ee187e9c582ba6
```
2 - Perform SHA-256 hashing on the public key.
```sh
$ bx sha256 0450863ad64a87ae8a2fe83c1af1a8403cb53f53e486d8511dad8a04887e5b23522cd470243453a299fa9e77237716103abc11a1df38855ed6f2ee187e9c582ba6
```
```
600ffe422b4e00731a59557a5cca46cc183944191006324a447bdb2d98d4b408
```
3 - Perform RIPEMD-160 hashing on the result of SHA-256.
```sh
$ bx ripemd160 600ffe422b4e00731a59557a5cca46cc183944191006324a447bdb2d98d4b408
```
```
010966776006953d5567439e5e39f86a0d273bee
```
4 - Add version byte in front of RIPEMD-160 hash (0x00 for Main Network).
```
00010966776006953d5567439e5e39f86a0d273bee
```
5 - Perform SHA-256 hash on the extended RIPEMD-160 result.
```sh
$ bx sha256 00010966776006953d5567439e5e39f86a0d273bee
```
```
445c7a8007a93d8733188288bb320a8fe2debd2ae1b47f0f50bc10bae845c094
```
6 - Perform SHA-256 hash on the result of the previous SHA-256 hash.
```sh
$ bx sha256 445c7a8007a93d8733188288bb320a8fe2debd2ae1b47f0f50bc10bae845c094
```
```
d61967f63c7dd183914a4ae452c9f6ad5d462ce3d277798075b107615c1a8a30
```
7 - Take the first 4 bytes of the second SHA-256 hash. This is the address checksum.
```
d61967f6
```
8 - Add the 4 checksum bytes from stage 7 at the end of extended RIPEMD-160 hash from stage 4. This is the 25-byte binary Bitcoin Address.
```
00010966776006953d5567439e5e39f86a0d273beed61967f6
```
9 - Convert the result from a byte string into a base58 string using Base58Check encoding. This is the most commonly used Bitcoin Address format.
```sh
$ bx base58-encode 00010966776006953d5567439e5e39f86a0d273beed61967f6
```
```
16UwLL9Risc3QfPqBUvKofHmBQ7wMtjvM
```

### Abbreviated Version
```sh
$ bx ec-to-public -u 18e14a7b6a307f426a94f8114701e7c8e774e7f9a47e2c2035db29a206321725 | bx sha256 | bx ripemd160 | bx address-encode
```
```
0450863ad64a87ae8a2fe83c1af1a8403cb53f53e486d8511dad8a04887e5b23522cd470243453a299fa9e77237716103abc11a1df38855ed6f2ee187e9c582ba6
600ffe422b4e00731a59557a5cca46cc183944191006324a447bdb2d98d4b408
010966776006953d5567439e5e39f86a0d273bee
16UwLL9Risc3QfPqBUvKofHmBQ7wMtjvM
```

### Command Equivalence
```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx bitcoin160 | bx address-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```
The same address results from the more general `base58check-encode` command in place of `address-encode`.
```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx bitcoin160 | bx base58check-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```
The same address results from the combination of the more general `wrap-encode` and `base58-encode` commands in place of `base58check-encode`.
```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx bitcoin160 | bx wrap-encode | bx base58-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
000423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b5728093a
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```
The same address results from the combination of the more general `sha256 ` and `ripemd160` commands in place of `bitcoin160`.
```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx sha256 | bx ripemd160 | bx wrap-encode | bx base58-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
bbd353249bf2360955621268b7db701454a20e7b5b2f42536c10a97712ad4895
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
000423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b5728093a
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```