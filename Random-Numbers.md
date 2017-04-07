With the exception of [cert-new](bx-cert-new), any BX command that requires a random number obtains that value as an argument. This places the responsibility of ensuring random number strength on end-users and also helps them understand the potential for problems.

> The `cert-new` command uses platform random number generation due to its reliance on the underlying [Curve ZMQ](http://curvezmq.org) implementation.

The [seed](bx-cert-new) command is provided as a convenience, and is the only command that generates randomness.
```sh
$ bx seed --bit_length 256
```
```
e4d28a5972ce0785477f39f58e424c5ef643b26894c50f8e024601f87736b8fe 
```
BX utilizes libbitcoin's deterministic ECDSA and as such requires no seed for signing.
