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
-f [--format]        The output format. Options are 'info', 'json', and  
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE58CHECK          The Base58Check value to decode. If not specified
                     the value is read from STDIN.
```
See also [base58check-encode](bx-base58check-encode).
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
version 42
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
### Example 3
```sh
$ bx base58check-decode 12ANjYr7zPnxRdZfnmC2e6jjHDpBY
```
```js
wrapper
{
    checksum 530125139
    payload 5361746f736869204e616b616d6f746f
    version 0
}
```
Notice that the following commands produce the equivalent result.
```sh
$ bx base58-decode 12ANjYr7zPnxRdZfnmC2e6jjHDpBY | bx wrap-decode
```
```js
005361746f736869204e616b616d6f746f5311991f
wrapper
{
    checksum 530125139
    payload 5361746f736869204e616b616d6f746f
    version 0
}
```
Extract the payload value.
```sh
$ bx base16-decode 5361746f736869204e616b616d6f746f
```
```
Satoshi Nakamoto
```
### Example 4
piped input
```sh
$ echo 12ANjYr7zPnxRdZfnmC2e6jjHDpBY | bx base58check-decode
```
```js
12ANjYr7zPnxRdZfnmC2e6jjHDpBY 
wrapper
{
    checksum 530125139
    payload 5361746f736869204e616b616d6f746f
    version 0
}
```