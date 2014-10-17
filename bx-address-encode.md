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
address breakdown
```sh
$ bx seed
```
```
9bb08de6bcc361df764c1edd9cc93059 
```
This produces a public key payment address generated using the `address-encode` command, which is limited to accepting a 160 bit payload.
```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx bitcoin160 | bx address-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```
The same address results from use of the more general `base58check-encode` command.
```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx bitcoin160 | bx base58check-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```
Same
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