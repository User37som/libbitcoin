Watch the network for transactions in which an address participates.
```sh
$ bx watch-address --help
```
```
Usage: bx watch-address [-h] [--config value] [--duration value]
[PAYMENT_ADDRESS]

Info: Watch the network for transactions in which an address
participates. Requires a Libbitcoin server connection.

Options (named):

-c [--config]        The path to the configuration settings file.
-d [--duration]      The duration of the watch in seconds, defaults to
                     600.
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

PAYMENT_ADDRESS      The participating payment address. If not specified
                     the address is read from STDIN.
```
This command supports [configuration settings](Configuration-Settings).

This command requires [libbitcoin-server](https://github.com/libbitcoin/libbitcoin-server) version 3.1.

This command reflects transactions created after the subscription is established.

> Type `ctrl-c` to terminate the watcher.

### Example 1
connecting to an Obelisk server (unsupported)
```sh
$ bx watch-address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
```
Bad stream
```
### Example 2
monitor donations to Satoshi
```sh
$ bx watch-address 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
```
This message will be written once the subscription is established.
```
Watching address: 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa...
```
For each new transaction that impacts the address a new line will be written to the console.