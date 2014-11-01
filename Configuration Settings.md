### Specifying a Configuration File
Not all BX commands use configuration settings, in fact most do not. However all commands process the configuration file if its path specified.

All commands accept a `--config` option. This allows any command line to specify a configuration file for use in that single execution.

If the `--config` option is not set the command will use the configuration file specified by the `BX_CONFIG` environment variable.

If neither the --config option nor the `BX_CONFIG` environment variable is set the command will use embedded default configuration settings. There is no default configuration file location.
### Default Configuration Settings
The BX [metadata file](https://github.com/libbitcoin/libbitcoin-explorer/blob/master/model/generate.xml) declares all valid configuration settings, their data types and descriptions. These values generated code that is used to build BX.

For convenience, the [example.cfg](https://github.com/libbitcoin/libbitcoin-explorer/blob/master/example.cfg) file is also populated with these values, although the metadata file is authoritative.
```ini
# Example Bitcoin Explorer (BX) configuration file.

[general]

# Only hd-new and stealth-encode currently use the testnet distinction, apart from swapping servers.
# The network to use, either 'mainnet' or 'testnet'. Defaults to 'mainnet'.
network = mainnet

# Number of times to retry contacting the server before giving up.
retries = 0

# Milliseconds to wait for a response from the server.
wait = 2000

[mainnet]

# The URL of the default mainnet Obelisk server.
url = tcp://obelisk-sol.airbitz.co:9091

[testnet]

# The URL of the default testnet Obelisk server.
url = tcp://obelisk-testnet.airbitz.co:9091
```

The file is not strictly an `ini` file although it is similar in structure. It is based on [Boost program options](http://www.boost.org/doc/libs/1_56_0/doc/html/program_options/overview.html#idp344521728).
### Exporting Settings
The [settings](bx-settings) command outputs all settings and values. When a path is specified on the command line or by environment variable, the values are populated accordingly.