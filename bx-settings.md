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
    network
    {
        channel_handshake_seconds 30
        connect_retries 0
        connect_timeout_seconds 5
        debug_file debug.log
        error_file error.log
        hosts_file hosts.cache
        identifier 3652501241
        seeds seed.bitnodes.io:8333,seed.bitcoinstats.com:8333,seed.bitcoin.sipa.be:8333,dnsseed.bluematt.me:8333,seed.bitcoin.jonasschnelli.ch:8333,dnsseed.bitcoin.dashjr.org:8333
    }
    server
    {
        cert_file ""
        connect_retries 0
        connect_timeout_seconds 5
        server_cert_key ""
        url tcp://obelisk.airbitz.co:9091
    }
    wallet
    {
        hd_private_version 76066276
        hd_public_version 76067358
        pay_to_public_key_hash_version 0
        pay_to_script_hash_version 5
        transaction_version 1
        wif_version 128
    }
}
```
### Example 2
--config bx-testnet.cfg
```sh
$ bx settings -c bx-testnet.cfg
```
```js
settings
{
    network
    {
        channel_handshake_seconds 30
        connect_retries 0
        connect_timeout_seconds 5
        debug_file debug.log
        error_file error.log
        hosts_file hosts.cache
        identifier 118034699
        seeds testnet-seed.alexykot.me:18333,testnet-seed.bitcoin.petertodd.org:18333,testnet-seed.bluematt.me:18333,testnet-seed.bitcoin.schildbach.de:18333
    }
    server
    {
        cert_file ""
        connect_retries 0
        connect_timeout_seconds 5
        server_cert_key ""
        url tcp://obelisk-testnet.airbitz.co:9091
    }
    wallet
    {
        hd_private_version 70615956
        hd_public_version 70617039
        pay_to_public_key_hash_version 111
        pay_to_script_hash_version 196
        transaction_version 1
        wif_version 239
    }
}
```

> This presumes the existence of `bx-testnet.cfg` with the above settings.

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
    logging
    {
        debug_file debug.log
        error_file error.log
    }
    mainnet
    {
        cert_file ""
        server_cert_key ""
        url tcp://obelisk.unsystem.net:9091
    }
    testnet
    {
        cert_file ""
        server_cert_key ""
        url tcp://obelisk.unsystem.net:10091
    }
}
```

> This presumes the existence of `MyConfig/bx.cfg` with the above settings.