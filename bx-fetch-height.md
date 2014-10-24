Get the last block height.
```sh
$ bx fetch-height --help
```
```
Usage: bx fetch-height [-h] [--config VALUE]                             

Info: Get the last block height. Requires an Obelisk server connection.  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
```
This command supports [configuration settings](Configuration-Settings).
### Example 1
```sh
$ bx fetch-height
```
```
325956
```

> The height will increase as more blocks are mined and may vary slightly between servers.