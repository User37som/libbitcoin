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
### Example 3
public server status
```sh
$ bx settings
```
```
general.retries = 0
general.testnet = false
general.wait = 10000
server.url = tcp://obelisk.unsystem.net:9091
```
The timeout has been increased to 10 seconds. The `server.url` value will be overridden by each command below. The `testnet` setting doesn't affect these calls.
```sh
$ servers.bat
```
```
$ bx fetch-height tcp://obelisk.unsystem.net:9091 
327053

$ bx fetch-height tcp://obelisk.unsystem.net:8081 
timed out

$ bx fetch-height tcp://obelisk.coinkite.com:9091 
327053

$ bx fetch-height tcp://obelisk.bysh.me:9091 
327053

$ bx fetch-height tcp://obelisk.ottrbutt.com:9091 
timed out

$ bx fetch-height tcp://obelisk-baltic.airbitz.co:9091 
327053

$ bx fetch-height tcp://obelisk-crate.airbitz.co:9091 
327053

$ bx fetch-height tcp://obelisk-sol.airbitz.co:9091 
327053

$ bx fetch-height tcp://obelisk-virpus.airbitz.co:9091 
327053

$ bx fetch-height tcp://37.139.11.99:9091 
timed out

$ bx fetch-height tcp://178.79.185.162:9091 
timed out

$ bx fetch-height tcp://85.25.198.97:10091 
304457

$ bx fetch-height tcp://obelisk-testnet.airbitz.co:9091 
304529

$ bx fetch-height tcp://preacher.veox.pw:9091 
304529
```