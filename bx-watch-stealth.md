Watch the network for transactions by stealth prefix.
```sh
$ bx watch-stealth--help
```
```
Usage: bx watch-stealth [-h] [--config value] [--duration value] [PREFIX]

Info: Watch the network for transactions by stealth prefix. Requires a
Libbitcoin server connection.

Options (named):

-c [--config]        The path to the configuration settings file.
-d [--duration]      The duration of the watch in seconds, defaults to
                     600.
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

PREFIX               The Base2 stealth prefix to watch. If not specified
                     the prefix is read from STDIN.
```
This command supports [configuration settings](Configuration-Settings).

This command requires [libbitcoin-server](https://github.com/libbitcoin/libbitcoin-server) version 3.1.

This command reflects transactions created after the subscription is established.

> Type `ctrl-c` to terminate the watcher.

### Example 1
connecting to an Obelisk server (unsupported)
```sh
$ bx watch-stealth 01010101
```
```
Bad stream
```
### Example 2
monitor a stealth prefix
```sh
$ bx watch-address 01010101
```
This message will be written once the subscription is established.
```
Watching stealth prefix: 01010101...
```
For each new transaction that may contain a payment pertaining to the prefix a new line will be written to the console.