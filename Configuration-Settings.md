### Specifying a Configuration File
Not all BX commands use configuration settings, in fact most do not. However all commands process the configuration file if its path is specified.

The path to the configuration settings file is specified by the `--config` command line option, the `BX_CONFIG` environment variable, or by default as follows:

* Linux/OSX (prefix): `<prefix>/etc/libbitcoin/bx.cfg`
* Linux/OSX (default): `/usr/local/etc/libbitcoin/bx.cfg`
* Windows: `%ProgramData%\libbitcoin\bx.cfg`

The Windows directory is hidden by default. If the file is not found default values are loaded. If the file is contains invalid settings an error is returned via STDERR. If any setting is not specified its default is loaded.

### Default Configuration Settings

For convenience, the [bx.cfg](https://github.com/libbitcoin/libbitcoin-explorer/blob/version2/data/bx.cfg) file is populated with all default settings values.
```ini
# Bitcoin Explorer (BX) configuration file.

[general]
# Only hd-new and stealth-encode currently use the testnet distinction, apart from swapping servers.
# The network to use, either 'mainnet' or 'testnet'. Defaults to 'mainnet'.
network = mainnet
# Number of times to retry contacting the server before giving up.
retries = 0
# Milliseconds to wait for a response from the server.
wait = 2000

[logging]
# The path to the debug log file, used by send-tx-p2p.
debug_file = debug.log
# The path to the error log file, used by send-tx-p2p.
error_file = error.log

[mainnet]
# The URL of the default mainnet Obelisk server.
url = tcp://obelisk.airbitz.co:9091
# The Z85-encoded public key of the server certificate.
# server_cert_key = 
# The path to the ZPL-encoded client private certificate file.
# cert_file = 

[testnet]
# The URL of the default testnet Obelisk server.
url = tcp://obelisk-testnet.airbitz.co:9091
# The Z85-encoded public key of the server certificate.
# server_cert_key = 
# The path to the ZPL-encoded client private certificate file.
# cert_file = 
```

The file is not strictly an `ini` file although it is similar in structure. It is based on [Boost program options](http://www.boost.org/doc/libs/1_56_0/doc/html/program_options/overview.html#idp344521728).

### Exporting Settings
The [settings](bx-settings) command outputs all settings and values for the configuration file in use.