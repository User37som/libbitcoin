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
-h [--help]          Get a description and instructions for this
                     command.
-v [--version]       The desired Bitcoin address version.

Arguments (positional):

RIPEMD160            The Base16 hash to convert. If not specified the
                     value is read from STDIN.
```
### Example 1
```sh
$ bx address-encode 
```
```

```