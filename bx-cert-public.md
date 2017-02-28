Derive a Curve ZMQ public key for use with a Libbitcoin server.
```sh
$ bx cert-public --help
```
```
Usage: bx cert-public [-h] [--config value] [PRIVATE_KEY]

Info: Derive a Curve ZMQ public key for use with a Libbitcoin server.

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

PRIVATE_KEY          The private key from which to derive the public key.     
```
Public certificates are consumed directly by [Libbitcoin Server](https://github.com/libbitcoin/libbitcoin-server) for client identity and by BX for server identity.

See also [cert-new](bx-cert-new).
### Example 1
```sh
$ bx.exe cert-public "A6hgo]R8<48/xB3yfd5x]mt-a9u/*P^j$$K)SBR@"
```
```
2!{^*kaa:gU]z2/Jy/4N5h2o=F[WE=2V0gi(Btqo
```