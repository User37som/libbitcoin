Convert a Base16 value to binary data.
```sh
$ bx base16-decode --help
```
```
Usage: bx base16-decode [-h] [--config VALUE] [BASE16]

Info: Convert a Base16 value to binary data.

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE16               The Base16 value to decode as binary data. If not
                     specified the value is read from STDIN.
```
This command is a simple [hexadecimal](http://en.wikipedia.org/wiki/Hexadecimal) decoder.

Base-16 is not case sensitive. In other words the letter F and the f are the same value.
### Example 1
```sh
$ bx base16-decode 5361746f736869204e616b616d6f746f
```
```
Satoshi Nakamoto
```
### Example 2
upper case encoding
```sh
$ bx base16-decode 5361746F736869204E616b616d6F746F
```
```
Satoshi Nakamoto
```
### Example 3
[FIPS 180-2 SHA-1 Vector A](http://www.nsrl.nist.gov/testdata)
```sh
$ bx base16-decode 616263
```
```
abc
```
### Example 4
[FIPS 180-2 SHA-1 Vector B](http://www.nsrl.nist.gov/testdata)
```sh
$ bx base16-decode 6162636462636465636465666465666765666768666768696768696a68696a6b696a6b6c6a6b6c6d6b6c6d6e6c6d6e6f6d6e6f706e6f7071
```
```
abcdbcdecdefdefgefghfghighijhijkijkljklmklmnlmnomnopnopq
```
### Example 5
pipe commands, round trip
```sh
$ bx base16-encode "Satoshi Nakamoto" | bx base16-decode
```
```
5361746f736869204e616b616d6f746f
Satoshi Nakamoto
```