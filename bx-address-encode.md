Convert a RIPEMD160 value to a Bitcoin address.
```sh
$ bx address-encode --help
```
```
Usage: bx address-encode [-h] [--config VALUE] [--version VALUE]
[RIPEMD160]

Info: Convert a RIPEMD160 value to a Bitcoin address.

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this command.
-v [--version]       The desired Bitcoin address version.

Arguments (positional):

RIPEMD160            The Base16 hash to convert. If not specified the
                     value is read from STDIN.
```
See the [list of Bitcoin address prefixes](https://en.bitcoin.it/wiki/List_of_address_prefixes) for a detailed description of `version`.
### Example 1
```sh
$ bx address-encode b472a266d0bd89c13706a4132ccfb16f7c3b9fcb
```
```
1HT7xU2Ngenf7D4yocz2SAcnNLW7rK8d4E
```
### Example 2
--version 42
```sh
$ bx address-encode -v 42 b472a266d0bd89c13706a4132ccfb16f7c3b9fcb
```
```
JBeTK2YUWEFTTQvcqEyQoS3poXKjjc1oEP
```
### Example 3
[public key hash payment address](https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses) composition
```sh
$ bx ec-to-public -u 18e14a7b6a307f426a94f8114701e7c8e774e7f9a47e2c2035db29a206321725
```
```
0450863ad64a87ae8a2fe83c1af1a8403cb53f53e486d8511dad8a04887e5b23522cd470243453a299fa9e77237716103abc11a1df38855ed6f2ee187e9c582ba6
```
```sh
$ bx sha256 0450863ad64a87ae8a2fe83c1af1a8403cb53f53e486d8511dad8a04887e5b23522cd470243453a299fa9e77237716103abc11a1df38855ed6f2ee187e9c582ba6
```
```
600ffe422b4e00731a59557a5cca46cc183944191006324a447bdb2d98d4b408
```
### Example 4
equivalent piped commands
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