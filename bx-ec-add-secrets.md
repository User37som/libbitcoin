Calculate the EC function (SECRET + SECRET) % curve-order. 
```sh
$ bx ec-add-secrets --help
```
```
Usage: bx ec-add-secrets [-h] [--config VALUE] [SECRET]...               

Info: Calculate the EC function (SECRET + SECRET) % curve-order.         

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SECRET               The set of Base16 secrets to add. If not specified  
                     the secrets are read from STDIN.
```
# Example 1
```sh
$ bx
```
```
```