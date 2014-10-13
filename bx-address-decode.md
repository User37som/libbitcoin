Convert a Bitcoin address to its component parts.
```sh
$ bx address-decode --help
```
```
Usage: bx address-decode [-h] [--config VALUE] [--format VALUE]
[BITCOIN_ADDRESS]

Info: Convert a Bitcoin address to its component parts.

Options (named):
01234567890123456789012345678901234567890123456789012345678901234567890123
-c [--config]        The path to the configuration settings file.
-f [--format]        The output format. Options are 'json', 'xml', 'info'
                     or 'native', defaults to native.
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BITCOIN_ADDRESS      The Bitcoin address to convert. If not specified the
                     address is read from STDIN.
```
### Example 1
```sh
$ bx address-decode 1HT7xU2Ngenf7D4yocz2SAcnNLW7rK8d4E
```
```js
wrapper
{
    checksum 1476364070
    payload b472a266d0bd89c13706a4132ccfb16f7c3b9fcb
    version 0
}
```