#### Command Line

BX uses source code generation and Boost's [program_options](http://www.boost.org/doc/libs/1_49_0/doc/html/program_options/overview.html) library to bind command line parameters to strongly-typed command class properties.

Command headers are generated from metadata during development. The metadata include full definition for all command parameters, including name, shortcut, data type, order, cardinality, optionality, default value, help description, file input delegation, fallback to STDIN and definition for localized messages.
```xml
<command symbol="hd-private" category="WALLET">
    <option name="help" description="Derive a child HD (BIP32) private key from another HD private key." />
    <option name="hard" shortcut="d" description="Signal to create a hardened key." />
    <option name="index" type="uint32_t" description="The HD index, defaults to zero." />
    <argument name="HD_PRIVATE_KEY" stdin="true" type="hd_private" description="The parent HD private key.  If not specified the key is read from STDIN." />
</command>
```
Input processing is handled in shared code and generated headers. All values are available to command implementation via strongly-typed getters on the command class:
```c++
// command implementation
console_result invoke(ostream& output, ostream& error)
{
    // bound getters
    auto hard = get_hard_option();
    auto index = get_index_option();
    auto& secret = get_hd_private_key_argument();

     /* command logic omitted */

    return console_result::okay;
}
```
Corresponding setters enable library consumers to execute BX methods directly. This is the access technique used by all tests:
```c++
BOOST_AUTO_TEST_CASE(hd_private__invoke__mainnet_vector2_m_0_2147483647h_1_2147483646h__okay_output)
{
    BX_DECLARE_COMMAND(hd_private);
    
    // corresponding setters
    command.set_hard_option(true);
    command.set_index_option(2147483646);
    command.set_hd_private_key_argument({ "xprv9zFnWC6h2cLgpmSA46vutJzBcfJ8yaJGg8cX1e5StJh45BBciYTRXSd25UEPVuesF9yog62tGAQtHjXajPPdbRCHuWS6T8XA2ECKADdw4Ef" });
    
    BX_REQUIRE_OKAY(command.invoke(output, error));
    BX_REQUIRE_OUTPUT("xprvA1RpRA33e1JQ7ifknakTFpgNXPmW2YvmhqLQYMmrj4xJXXWYpDPS3xz7iAxn8L39njGVyuoseXzU6rcxFLJ8HFsTjSyQbLYnMpCqE2VbFWc\n");
}
```

#### Standard and File Input

In most commands the option is available to load the primary input parameter via [STDIN](http://wikipedia.org/wiki/Standard_streams#Standard_input_.28stdin.29). In many cases the input value can optionally be read from STDIN. Multi-valued inputs supported in STDIN treat any [whitespace](http://en.wikipedia.org/wiki/Whitespace_character) as a separator.

#### Configuration Settings

BX uses Boost's [program_options](http://www.boost.org/doc/libs/1_49_0/doc/html/program_options/overview.html) library to bind configuration settings to strongly-typed application level properties. Settings values are read into base command properties generated from the following metadata.
```xml
<configuration section="general">
    <!-- Only hd-new and stealth-encode currently use the testnet distinction, apart from swapping servers. -->
    <setting name="network" default="mainnet" description="The network to use, either 'mainnet' or 'testnet'. Defaults to 'mainnet'." />
    <setting name="retries" type="byte" description="Number of times to retry contacting the server before giving up." />
    <setting name="wait" default="2000" type="uint32_t" description="Milliseconds to wait for a response from the server." />
</configuration>

<configuration section="logging">
    <setting name="debug" type="path"  default="debug.log" description="The path to the debug log file, used by send-tx-p2p." />
    <setting name="error" type="path"  default="error.log" description="The path to the error log file, used by send-tx-p2p." />
</configuration>

<configuration section="mainnet">
    <setting name="url" type="uri" default="tcp://obelisk.airbitz.co:9091" description="The URL of the Obelisk mainnet server." />
</configuration>

<configuration section="testnet">
    <setting name="url" type="uri"  default="tcp://obelisk-testnet.airbitz.co:9091" description="The URL of the Obelisk testnet server." />
</configuration>
```
The implementation supports a two level hierarchy of settings using "sections" to group settings, similar to an `.ini` file:
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
debug = debug.log

# The path to the error log file, used by send-tx-p2p.
error = error.log

[mainnet]

# The URL of the default mainnet Obelisk server.
url = tcp://obelisk.airbitz.co:9091

[testnet]

# The URL of the default testnet Obelisk server.
url = tcp://obelisk-testnet.airbitz.co:9091
```
The path to the configuration settings file is specified by the `--config` command line option, the `BX_CONFIG` environment variable, or by default as follows:

Linux/OSX (prefix): `<prefix>/etc/libbitcoin/bx.cfg`
Linux/OSX (default): `/usr/local/etc/libbitcoin/bx.cfg`
Windows: `%ProgramData%\libbitcoin\bx.cfg`

The Windows directory is hidden by default. If the file is not found default values are loaded. If the file is contains invalid settings an error is returned via STDERR. If any setting is not specified its default is loaded.

The BX `settings` command shows the current value of all configuration settings.

#### Environment Variables

BX uses Boost's [program_options](http://www.boost.org/doc/libs/1_49_0/doc/html/program_options/overview.html) library to bind environment variables. All BX environment variables are prefixed with `BX_`. Currently environment variables are bound explicitly (i.e. bindings are not generated from metadata).

`BX_CONFIG` is the only bound environment variable. BX uses a Boost feature to tie the environment variable and the command line option of the same identity (i.e. `--config`). Command line options have precedence if both set.