Display the loaded configuration settings.  
```sh
$ bx settings --help
```
```
Usage: bx settings [-h] [--config VALUE]                                 

Info: Display the loaded configuration settings.                         

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
```
### Example 1
defaults
```sh
$ bx settings
```
```
general.retries = 0
general.testnet = false
general.wait = 2000
server.url = tcp://obelisk.unsystem.net:9091
```
### Example 1
--config bx.ini
```sh
bx settings -c bx.ini
```
```
general.retries = 2
general.testnet = false
general.wait = 10000
server.url = tcp://obelisk-sol.airbitz.co:9091
```

> This presumes a file named `bx.ini,` in the current directory with the above settings.