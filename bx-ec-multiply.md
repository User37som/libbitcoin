Calculate the EC product (POINT * SECRET).
```sh
$ bx ec-multiply --help
```
```
Usage: bx ec-multiply [-h] [--config VALUE] POINT SECRET                 

Info: Calculate the EC product (POINT * SECRET).                         

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

POINT                The Base16 EC point to multiply.                    
SECRET               The Base16 EC secret to multiply.
```
### Example 1
```sh
$ bx ec-multiply 021bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
02da5629b7902abcfc166b30eda4cc6b2702b5d0bb867217614101caa710f0753b
```