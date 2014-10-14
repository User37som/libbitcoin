Convert a Base58Check value to Base16.
```sh
$ bx base58check-decode --help
```
```
Usage: bx base58check-decode [-h] [--config VALUE] [--format VALUE]
[BASE58CHECK]

Info: Convert a Base58Check value to Base16.

Options (named):

-c [--config]        The path to the configuration settings file.
-f [--format]        The output format. Options are 'json', 'xml', 'info'
                     or 'native', defaults to native.
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE58CHECK          The Base58Check value to decode. If not specified
                     the value is read from STDIN.
```
### Example 1
version 0
```sh
$ bx base58check-decode 173RKgkk7fMbYUYBGyyAHeZ6rwfKRMn17h7DtGsmpEdab8TV6UB
```
```js
wrapper
{
    checksum 1020266843
    payload 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    version 0
}
```
### Example 2
version 42 (same payload)
```sh
$ bx base58check-decode 7DTXS6pY6a98XH2oQTZUbbd1Z7P4NzkJqfraixprPutXQVTkwBGw
```
```js
wrapper
{
    checksum 3840642601
    payload 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    version 42
}
```