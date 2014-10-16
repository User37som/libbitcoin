Generate a pseudorandom seed.

> WARNING: Pseudorandom seeds can introduce weakness into your keys. This command is provided as a convenience. 

```sh
$ bx seed --help
```
```
Usage: bx seed [-h] [--bit_length VALUE] [--config VALUE]                

Info: Generate a pseudorandom seed.                                      

Options (named):

-b [--bit_length]    The length of the seed in bits. Must be divisible by
                     8 and must not be less than 128.                    
-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
```
# Example 1
```sh
$ bx seed --help
```
```
```