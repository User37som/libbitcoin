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
```sh
$ bx base58check-decode
```
```

```
### Example 2
```sh
$ bx base58check-decode
```
```

```