All BX commands accept a `--config` option. This allows any command line to specify a configuration file for use in that single execution.

If the `--config` option is not set the command will use the configuration file specified by the `BX_CONFIG` environment variable.

If neither the --config option nor the `BX_CONFIG` environment variable is set the command will use default configuration settings. There is no default configuration file location.