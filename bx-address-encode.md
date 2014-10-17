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
piped commands
```sh
$ 
```
```

```