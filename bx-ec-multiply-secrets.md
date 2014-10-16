Calculate the EC function (SECRET * SECRET) % curve-order.
```sh
$ bx ec-multiply-secrets --help
```
```
Usage: bx ec-multiply-secrets [-h] [--config VALUE] [SECRET]...          

Info: Calculate the EC function (SECRET * SECRET) % curve-order.         

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SECRET               The set of Base16 EC secrets to multiply. If not    
                     specified the secrets are read from STDIN.
```
# Example 1
one secret (i.e. SECRET^1)
```sh
$ bx ec-multiply-secrets 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
# Example 2
two secrets (i.e. SECRET^1)
```sh
$ bx ec-multiply-secrets 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
e5b87c7917f8414d2fa5caa32ea61b06fca755fee6a113179db70f5e0d5393ba
```