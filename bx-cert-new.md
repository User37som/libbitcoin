Create a Curve ZMQ private key for use with a Libbitcoin server.
```sh
$ bx cert-new --help
```
```
Usage: bx cert-new [-h] [--config value]

Info: Create a Curve ZMQ private key for use with a Libbitcoin server.
WARNING: entropy is obtained from the underlying platform.

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this command.           
```
Private certificates are consumed directly by [Libbitcoin Server](https://github.com/libbitcoin/libbitcoin-server) for server identity and by BX for client identity.

See also [cert-public](bx-cert-public).
### Example 1
```sh
$ bx cert-new
```
```
A6hgo]R8<48/xB3yfd5x]mt-a9u/*P^j$$K)SBR@
```