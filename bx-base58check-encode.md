Convert a Base16 value to Base58Check.
```sh
$ bx base58check-encode --help
```
```
Usage: bx base58check-encode [-h] [--config VALUE] [--version VALUE]
[BASE16]

Info: Convert a Base16 value to Base58Check.

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this command.
-v [--version]       The desired version number.

Arguments (positional):

BASE16               The Base16 value to Base58Check encode. If not
                     specified the value is read from STDIN.
```
See [Base58Check encoding](https://en.bitcoin.it/wiki/Base58Check_encoding) for a detailed description of the encoding.
### Example 1
```sh
$ bx base58check-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
173RKgkk7fMbYUYBGyyAHeZ6rwfKRMn17h7DtGsmpEdab8TV6UB
```
### Example 2
version 42
```sh
$ bx base58check-encode -v 42 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
7DTXS6pY6a98XH2oQTZUbbd1Z7P4NzkJqfraixprPutXQVTkwBGw
```
### Example 3
piped commands
```sh
$ bx base16-encode "Satoshi Nakamoto" | bx base58check-encode
```
```
5361746f736869204e616b616d6f746f
12ANjYr7zPnxRdZfnmC2e6jjHDpBY
```