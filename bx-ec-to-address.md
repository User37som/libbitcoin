Convert an EC public key to a Bitcoin address.
```sh
$ bx ec-to-address --help
```
```
Usage: bx ec-to-address [-h] [--config VALUE] [--version VALUE]         
[EC_PUBLIC_KEY]

Info: Convert an EC public key to a Bitcoin address.

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
$ bx ec-to-address -v42 0447140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36e87bb04f401be3b770a0f3e2267a6c3b14a3074f6b5ce4419f1fcdc1ca4b1cb6
```
```
J3JahRViQGWq5X5KhPSyB1YdZwBu2EQzFR
```
### Example 5
piped commands (note that `$ bx seed` produces random output)
```sh
$ bx seed -b 256 | bx ec-new | bx ec-to-public | bx ec-to-address -v42
```
```
e9c26cad54bf344da82a1f47cd2359229ba4d4524d61f492457a457b00b49783
83cc0edb442f997dc6e900c3f224e2808fcf22dec82cdfe0523ebf4a5b9029da
02d6a11f0b8f71459c1c41da5d788a149a2cb27f571d8d2777d7870c698dfa564e
J7MReAaWQrmxR4vL65kWMJUdCPFABkYm8z
```