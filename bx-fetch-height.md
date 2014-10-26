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
The `testnet` setting doesn't affect these calls. The `wait` period has been increased to `10000` milliseconds. The `server.url` value will be overridden by each command below.
```sh
$ ./servers.sh
```
```
Development Servers
------------------------------------------------------
tcp://obelisk.unsystem.net:9091
327055
tcp://obelisk.unsystem.net:8081
Connection timed out

Production Servers
------------------------------------------------------
tcp://obelisk.coinkite.com:9091
327055
tcp://obelisk.bysh.me:9091
327055
tcp://obelisk.ottrbutt.com:9091
Connection timed out
tcp://obelisk-baltic.airbitz.co:9091
327055
tcp://obelisk-crate.airbitz.co:9091
327055
tcp://obelisk-sol.airbitz.co:9091
327055
tcp://obelisk-virpus.airbitz.co:9091
327055

Testing Servers
------------------------------------------------------
tcp://37.139.11.99:9091
Connection timed out

Testnet Servers
------------------------------------------------------
tcp://178.79.185.162:9091
Connection timed out
tcp://85.25.198.97:10091
304461
tcp://obelisk-testnet.airbitz.co:9091
304534
tcp://preacher.veox.pw:9091
304534
```
The example script `servers.sh` is based on the following pattern.
```sh
echo Development Servers
echo ------------------------------------------------------
echo tcp://obelisk.unsystem.net:9091
bx fetch-height tcp://obelisk.unsystem.net:9091
```