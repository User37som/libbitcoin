Display the loaded configuration settings.  
```sh
$ bx settings --help
```
```
Usage: bx settings [-h] [--config VALUE] [--format VALUE]                

Info: Display the loaded configuration settings.                         

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.
```
If settings are not specified in a configuration file the defaults are populated.
### Example 1
defaults
```sh
$ bx settings
```
```js
settings
{
    general
    {
        network mainnet
        retries 0
        wait 2000
    }
    mainnet
    {
        url tcp://obelisk.unsystem.net:9091
    }
    testnet
    {
        url tcp://obelisk.unsystem.net:10091
    }
}
```
### Example 2
--config bx.ini
```sh
$ bx settings -c bx.cfg
```
```js
settings
{
    general
    {
        network testnet
        retries 1
        wait 10000
    }
    mainnet
    {
        url tcp://obelisk-sol.airbitz.co:9091
    }
    testnet
    {
        url tcp://obelisk-testnet.airbitz.co:9091
    }
}
```

> This presumes the existence of `bx.cfg` with the above settings.

### Example 3
environment variable `BX_CONFIG=MyConfig/bx.cfg`
```sh
$ bx settings
```
```js
settings
{
    general
    {
        network mainnet
        retries 0
        wait 10000
    }
    mainnet
    {
        url tcp://obelisk-sol.airbitz.co:9091
    }
    testnet
    {
        url tcp://obelisk.unsystem.net:10091
    }
}
```

> This presumes the existence of `MyConfig/bx.cfg` with the above settings.