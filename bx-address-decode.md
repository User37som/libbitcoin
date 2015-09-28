Convert a Bitcoin address to its component parts.
```sh
$ bx address-decode --help
```
```
Usage: bx address-decode [-h] [--config VALUE] [--format VALUE]
[BITCOIN_ADDRESS]

Info: Convert a Bitcoin address to its component parts.

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json', and  
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BITCOIN_ADDRESS      The Bitcoin address to convert. If not specified the
                     address is read from STDIN.
```
These examples demonstrate the use of the `--format` option, which is available on a number of commands. The default format for any command is `info`. The `info` format is similar to `json` but optimized for human readability.

See also [address-encode](bx-address-encode).
### Example 1
```sh
$ bx address-decode 1HT7xU2Ngenf7D4yocz2SAcnNLW7rK8d4E
```
```js
wrapper
{
    checksum 2743498322
    payload b472a266d0bd89c13706a4132ccfb16f7c3b9fcb
    version 0
}
```
### Example 2
--format json
```sh
$ bx address-decode -f json 1HT7xU2Ngenf7D4yocz2SAcnNLW7rK8d4E
```
```js
{
    "wrapper": {
        "checksum": "2743498322",
        "payload": "b472a266d0bd89c13706a4132ccfb16f7c3b9fcb",
        "version": "0"
    }
}
```
### Example 3
--format xml
```sh
$ bx address-decode -f xml 1HT7xU2Ngenf7D4yocz2SAcnNLW7rK8d4E
```
```xml
<?xml version="1.0" encoding="utf-8"?>
<wrapper><checksum>2743498322</checksum><payload>b472a266d0bd89c13706a4132ccfb16f7c3b9fcb</payload><version>0</version></wrapper>
```
### Example 4
testnet address (version 111)
```sh
$ bx address-decode mwy5FX7MVgDutKYbXBxQG5q7EL6pmhHT58
```
```js
wrapper
{
    checksum 1475514977
    payload b472a266d0bd89c13706a4132ccfb16f7c3b9fcb
    version 111
}
```
### Example 5
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-public | bx ec-to-address | bx address-decode
```
```js
f0630cf3954c95d53a021ee0bb6668dd
e6d6c2ff0fec07704a57c5f8baaef838ab8254ca29b33f504cec73064548b925
03fa282f3907f0929782279a23d6e2ddda2c8309eba0c2f3b00ccb9f9e3d0a5606
1PCZAeAsyyeDDFtfdce3p5ppkAfmFBDTsf
wrapper
{
    checksum 1659491557
    payload f382319f0335055fd7501c0ad8300aba25fa8c05
    version 0
}
```