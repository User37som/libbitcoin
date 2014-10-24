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

# Set to true for testnet operation. This option is EXPERIMENTAL because other 
# libraries on which this application depends must currently be compiled with 
# the testnet flag to ensure complete testnet semantics.
testnet = false

# Number of times to retry contacting the server before giving up.
retries = 0

# Milliseconds to wait for a response from the server.
wait = 2000

[server]

# The URI of the obelisk server.
address = tcp://obelisk-sol.airbitz.co:9091

# The base-16 encoded public key of the server.
public-key =
```