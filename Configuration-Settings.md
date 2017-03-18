### Specifying a Configuration File
Not all BX commands use configuration settings, in fact most do not. However all commands process the configuration file if its path is specified.

The path to the configuration settings file is specified by the `--config` command line option, the `BX_CONFIG` environment variable, or by default as follows:

* Linux/OSX (prefix): `<prefix>/etc/libbitcoin/bx.cfg`
* Linux/OSX (default): `/usr/local/etc/libbitcoin/bx.cfg`
* Windows: `%ProgramData%\libbitcoin\bx.cfg`

The Windows directory is hidden by default. If the specified file is not found default values are loaded. If the file contains invalid settings an error is returned via STDERR. If any setting is not specified its default is loaded.

BX uses libbitcoin's wrappers over Boost's [program_options](http://www.boost.org/doc/libs/1_49_0/doc/html/program_options/overview.html) library to bind configuration settings. The implementation supports a two level hierarchy of settings using "sections" to group settings, similar to an `.ini` file.

### Default Configuration Settings

For convenience, the [bx.cfg](https://github.com/libbitcoin/libbitcoin-explorer/blob/version3/data/bx.cfg) file is populated with all default settings values.

### Exporting Settings
The [settings](bx-settings) command outputs all settings and values for the configuration file in use.