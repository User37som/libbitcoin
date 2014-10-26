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
### Example 2
--config bx.ini
```sh
$ bx settings -c bx.cfg
```
```
general.retries = 2
general.testnet = false
general.wait = 10000
server.url = tcp://obelisk-sol.airbitz.co:9091
```

> This presumes a file named `bx.cfg` in the current directory with the above settings.

### Example 3
environment variable `BX_CONFIG=bx.cfg`
```sh
$ bx settings
```
```
general.retries = 2
general.testnet = false
general.wait = 10000
server.url = tcp://obelisk-sol.airbitz.co:9091
```

> This presumes a file named `bx.cfg` in the current directory with the above settings.