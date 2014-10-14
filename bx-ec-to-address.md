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
### Example 1
compressed key
```sh
$ bx ec-to-address 0247140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36
```
```
1EKJFK8kBmasFRYY3Ay9QjpJLm4vemJtC1
```
### Example 2
uncompressed key
```sh
$ bx ec-to-address 0447140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36e87bb04f401be3b770a0f3e2267a6c3b14a3074f6b5ce4419f1fcdc1ca4b1cb6
```
```
197FLrycah42jKDgfmTaok7b8kNHA7R2ih
```