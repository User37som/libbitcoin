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
### Example 1
one secret (1 * SECRET)
```sh
$ bx ec-add-secrets 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
### Example 2
two same secrets (2 * SECRET)
```sh
$ bx ec-add-secrets 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
375709cd0fc6ca29dd5eb402f861a6583eb3ba9d4cc53b4f2e1946e8a27ba00c
```
### Example 3
three same secrets (3 * SECRET)
```sh
$ bx ec-add-secrets 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
53028eb397aa2f3ecc0e0e04749279845e0d97ebf327d8f6c525ea5cf3b97012
```
### Example 4
two secrets (SECRET + (2 * SECRET))
```sh
$ bx ec-add-secrets 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 375709cd0fc6ca29dd5eb402f861a6583eb3ba9d4cc53b4f2e1946e8a27ba00c
```
```
53028eb397aa2f3ecc0e0e04749279845e0d97ebf327d8f6c525ea5cf3b97012
```
### Example 5
two secrets (SECRET + 1)
```sh
$ bx ec-add-secrets 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 0000000000000000000000000000000000000000000000000000000000000001
```
```
1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd007
```