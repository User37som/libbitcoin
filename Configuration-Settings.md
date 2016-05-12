**SOME SETTINGS BELOW APPLY TO VERSION3, WHICH IS NOT RELEASED**

### Specifying a Configuration File
Not all BX commands use configuration settings, in fact most do not. However all commands process the configuration file if its path is specified.

The path to the configuration settings file is specified by the `--config` command line option, the `BX_CONFIG` environment variable, or by default as follows:

* Linux/OSX (prefix): `<prefix>/etc/libbitcoin/bx.cfg`
* Linux/OSX (default): `/usr/local/etc/libbitcoin/bx.cfg`
* Windows: `%ProgramData%\libbitcoin\bx.cfg`

The Windows directory is hidden by default. If the specified file is not found default values are loaded. If the file contains invalid settings an error is returned via STDERR. If any setting is not specified its default is loaded.

### Default Configuration Settings

For convenience, the [bx.cfg](https://github.com/libbitcoin/libbitcoin-explorer/blob/version2/data/bx.cfg) file is populated with all default settings values.
```ini
# Bitcoin Explorer (BX) configuration file.

[wallet]
# The wallet import format (WIF) key version, defaults to 128.
wif_version = 128
# The hierarchical deterministic (HD) public key version, defaults to 76067358.
hd_public_version = 76067358
# The hierarchical deterministic (HD) private key version, defaults to 76066276.
hd_private_version = 76066276
# The pay-to-public-key-hash address version, defaults to 0.
pay_to_public_key_hash_version = 0
# The pay-to-script-hash address version, defaults to 5.
pay_to_script_hash_version = 5

[network]
# The magic number for message headers, defaults to 3652501241.
identifier = 3652501241
# The number of times to retry contacting a node, defaults to 0.
connect_retries = 0
# The time limit for connection establishment, defaults to 5.
connect_timeout_seconds = 5
# The time limit to complete the connection handshake, defaults to 30.
channel_handshake_seconds = 30
# The peer hosts cache file path, defaults to 'hosts.cache'.
hosts_file = hosts.cache
# The debug log file path, defaults to 'debug.log'.
debug_file = debug.log
# The error log file path, defaults to 'error.log'.
error_file = error.log
# A seed node for initializing the host pool, multiple allowed, defaults shown.
seed = seed.bitnodes.io:8333
seed = seed.bitcoinstats.com:8333
seed = seed.bitcoin.sipa.be:8333
seed = dnsseed.bluematt.me:8333
seed = seed.bitcoin.jonasschnelli.ch:8333
seed = dnsseed.bitcoin.dashjr.org:8333

[server]
# The URL of the mainnet Libbitcoin/Obelisk server.
url = tcp://obelisk.airbitz.co:9091
# The number of times to retry contacting a server, defaults to 0.
connect_retries = 0
# The time limit for connection establishment, defaults to 5.
connect_timeout_seconds = 5
# The Z85-encoded public key of the server certificate.
# server_certificate_key = 
# The path to the ZPL-encoded client private certificate file.
# client_certificate_file = 
```

The file is not strictly an `ini` file although it is similar in structure. It is based on [Boost program options](http://www.boost.org/doc/libs/1_56_0/doc/html/program_options/overview.html#idp344521728).

### Exporting Settings
The [settings](bx-settings) command outputs all settings and values for the configuration file in use.