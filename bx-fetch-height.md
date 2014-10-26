Get the last block height.
```sh
$ bx fetch-height --help
```
```
Usage: bx fetch-height [-h] [--config VALUE] [server-url]                

Info: Get the last block height. Requires an Obelisk server connection.  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

server-url           The URL of the Obelisk server to use. If not        
                     specified the URL is obtained from configuration    
                     settings or defaults.
```
This command supports [configuration settings](Configuration-Settings).

The height reported will increase as more blocks are mined and may vary slightly between servers.
### Example 1
```sh
$ bx fetch-height
```
```
325956
```
### Example 2
server-url, wrong port number
```sh
$ bx fetch-height tcp://obelisk.unsystem.net
```
```
timed out
```