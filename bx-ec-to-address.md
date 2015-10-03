Convert an EC public key to a payment address.
```sh
$ bx ec-to-address --help
```
```
Usage: bx ec-to-address [-h] [--config VALUE] [--version VALUE]         
[EC_PUBLIC_KEY]

Info: Convert an EC public key to a payment address.

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-v [--version]       The desired Bitcoin address version.                

Arguments (positional):

EC_PUBLIC_KEY        The Base16 EC public key to convert. If not         
                     specified the key is read from STDIN.
```
### Example 1
compressed key
```sh
$ bx ec-to-address 0247140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36
```
```
1EKJFK8kBmasFRYY3Ay9QjpJLm4vemJtC1
```
### Example 2
compressed key, --version 42
```sh
$ bx ec-to-address -v 42 0247140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36
```
```
J8Wdbser1M3fbdQB4nxXn1FLmwtYXKovfA
```
### Example 3
uncompressed key
```sh
$ bx ec-to-address 0447140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36e87bb04f401be3b770a0f3e2267a6c3b14a3074f6b5ce4419f1fcdc1ca4b1cb6
```
```
197FLrycah42jKDgfmTaok7b8kNHA7R2ih
```
### Example 4
uncompressed key, --version 42
```sh
$ bx ec-to-address -v 42 0447140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36e87bb04f401be3b770a0f3e2267a6c3b14a3074f6b5ce4419f1fcdc1ca4b1cb6
```
```
J3JahRViQGWq5X5KhPSyB1YdZwBu2EQzFR
```
### Example 5
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-public | bx ec-to-address
```
```
3f152b0e3c5806bd9cd2f7c833acd061
a927f06ad73c139d7f912c06700bc8ee8060ab0e5507e8119ddf56ad3dbb9576
03255c8998fbf7d3820d4c6c73996467080750eeb51f050214b65d16da8cf2b8dc
13ua8RRSxLpL5WL5cKUDepUCvJZgGWuKh7
```
> Note that `$ bx seed` produces random output.

### Example 6
*[Technical background of version 1 Bitcoin addresses]((https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses))*
```sh
$ bx ec-to-public -u 18e14a7b6a307f426a94f8114701e7c8e774e7f9a47e2c2035db29a206321725 | bx ec-to-address
```
```
0450863ad64a87ae8a2fe83c1af1a8403cb53f53e486d8511dad8a04887e5b23522cd470243453a299fa9e77237716103abc11a1df38855ed6f2ee187e9c582ba6
16UwLL9Risc3QfPqBUvKofHmBQ7wMtjvM
```