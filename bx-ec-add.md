Calculate the EC function POINT + (SECRET * curve-generator-point).
```sh
$ bx ec-add --help
```
```
Usage: bx ec-add [-h] [--config value] POINT [SECRET]

Info: Calculate the EC function POINT + (SECRET * curve-generator-point).

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

POINT                The Base16 EC point to add.
SECRET               The Base16 EC secret to add. If not specified the
                     secret is read from STDIN.
```
### Example 1
```sh
$ bx ec-add 021bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 1bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
0398dbb46779e5e82fc7422c874e2390f3e076500410481bd129927f78cfc455ac
```