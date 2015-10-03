Generate a pseudorandom seed.

> WARNING: Pseudorandom seeding can introduce [cryptographic weakness](http://cwe.mitre.org/data/definitions/338.html) into your keys. This command is provided as a convenience. 

```sh
$ bx seed --help
```
```
Usage: bx seed [-h] [--bit_length VALUE] [--config VALUE]                

Info: Generate a pseudorandom seed.                                      

Options (named):

-b [--bit_length]    The length of the seed in bits. Must be divisible by
                     8 and must not be less than 128, defaults to 192.   
-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
```
### Example 1
128 bit seed
```sh
$ bx seed
```
```
d915107990a42dfb2ea5762729002d47a4748e0f24aceb61
```
### Example 2
1024 bit seed
```sh
$ bx seed -b 1024
```
```
273a08cab80ec0326e315b1fe800b63556e3257571cb3d72cf4efc26926b9b73f8808d9cae65b2ba48a19417426a147905fe260338acf7d5f0a214557b440a9e7fb4c344f0867f44cb042b4e434820b9c6f338a136ca120a4324ae717c8f483813a8fbf3854117bd9a37b94811cc51a616a0a534ecb7acabcacc7993252f2c39
```
### Example 3
short seed error
```sh
$ bx seed -b 32
```
```
The seed size is not supported.
```