Convert binary data to Base16.
```sh
$ bx base16-encode --help
```
```
Usage: bx base16-encode [-h] [--config VALUE] [DATA]

Info: Convert binary data to Base16.

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

DATA                 The binary data to encode as Base16. This can be
                     text or any other data. If not specified the data is
                     read from STDIN.
```
This command is a simple [hexadecimal](http://en.wikipedia.org/wiki/Hexadecimal) encoder. This can be used to feed plain text or raw binary values into other commands as `base16` input.
### Example 1
```sh
$ bx base16-encode "Satoshi Nakamoto"
```
```
5361746f736869204e616b616d6f746f
```
### Example 2
[FIPS 180-2 SHA-1 Vector A](http://www.nsrl.nist.gov/testdata)
```sh
$ bx base16-encode abc
```
```
616263
```
### Example 3
[FIPS 180-2 SHA-1 Vector B](http://www.nsrl.nist.gov/testdata)
```sh
$ bx base16-encode abcdbcdecdefdefgefghfghighijhijkijkljklmklmnlmnomnopnopq
```
```
6162636462636465636465666465666765666768666768696768696a68696a6b696a6b6c6a6b6c6d6b6c6d6e6c6d6e6f6d6e6f706e6f7071
```
### Example 4
routed input, hash self
```sh
$ bx base16-encode < bx.exe | bx sha256
```
```
f9c8f0a86f772a2dd1adf7e43f427ec99e59084b4cd9b41861a2c9d84010575d
```