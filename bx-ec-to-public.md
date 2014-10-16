Derive the EC public key of an EC private key.
```sh
$ bx ec-to-public --help
```
```
Usage: bx ec-to-public [-hu] [--config VALUE] [EC_PRIVATE_KEY]

Info: Derive the EC public key of an EC private key. Defaults to the    
compressed public key format.

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-u [--uncompressed]  Derive using the uncompressed public key format.    

Arguments (positional):

EC_PRIVATE_KEY       The Base16 EC private key. If not specified the key 
                     is read from STDIN.
```
### Example 1
```sh
$ bx ec-to-public 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8
```
```
0247140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36
```
### Example 2
--uncompressed
```sh
$ bx ec-to-public -u 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8
```
```
0447140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36e87bb04f401be3b770a0f3e2267a6c3b14a3074f6b5ce4419f1fcdc1ca4b1cb6
```
### Example 2
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-public
```
```
2deeac24fa1b0678c71f2427400c35ac
1f31b7247933f36dde11610b32d473710aedca81f34d90137370366f5291c966
02daa7db1b30da2a9a457171f5861d98d055b3bb0f31316679766fd1c774519d2a
```