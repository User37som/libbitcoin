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
  <configuration section="wallet">
    <setting name="wif_version" type="byte" default="128" description="The wallet import format (WIF) key version, defaults to 128." />
    <setting name="hd_public_version" type="uint32_t" default="76067358" description="The hierarchical deterministic (HD) public key version, defaults to 76067358." />
    <setting name="hd_private_version" type="uint32_t" default="76066276" description="The hierarchical deterministic (HD) private key version, defaults to 76066276." />
    <setting name="pay_to_public_key_hash_version" type="byte" default="0" description="The pay-to-public-key-hash address version, defaults to zero." />
    <setting name="pay_to_script_hash_version" type="byte" default="5" description="The pay-to-script-hash address version, defaults to 5." />
    <setting name="transaction_version" type="byte" default="1" description="The transaction version, defaults to 1." />
  </configuration>

  <configuration section="network">
    <setting name="identifier" type="uint32_t" default="3652501241" description="The magic number for message headers, defaults to 3652501241." />
    <setting name="connect_retries" type="byte" default="0" description="The number of times to retry contacting a node, defaults to zero." />
    <setting name="connect_timeout_seconds" type="uint32_t" default="5" description="The time limit for connection establishment, defaults to 5." />
    <setting name="channel_handshake_seconds" type="uint32_t" default="30" description="The time limit to complete the connection handshake, defaults to 30." />
    <setting name="hosts_file" type="path" default="hosts.cache" description="The peer hosts cache file path, defaults to 'hosts.cache'." />
    <setting name="debug_file" type="path" default="debug.log" description="The debug log file path, defaults to 'debug.log'." />
    <setting name="error_file" type="path" default="error.log" description="The error log file path, defaults to 'error.log'." />
    <setting name="seed" type="endpoint" multiple="true" description="A seed node for initializing the host pool, multiple entries allowed." />
  </configuration>

  <configuration section="server">
    <setting name="url" type="endpoint" default="tcp://obelisk.airbitz.co:9091" description="The URL of the Libbitcoin/Obelisk server." />
    <setting name="connect_retries" type="byte" default="0" description="The number of times to retry contacting a server, defaults to zero." />
    <setting name="connect_timeout_seconds" default="5" type="uint32_t" description="The time limit for connection establishment, defaults to 5." />
    <setting name="server_cert_key" type="cert_key" description="The Z85-encoded public key of the server certificate." />
    <setting name="cert_file" type="path" description="The path to the ZPL-encoded client private certificate file." />
  </configuration>
```
The implementation uses a two level hierarchy of settings using "sections" to group settings, similar to an `.ini` file. A default [settings file](configuration-settings) is included with the build.

The BX `settings` command shows the current value of all configuration settings.

#### Environment Variables

BX uses Boost's [program_options](http://www.boost.org/doc/libs/1_49_0/doc/html/program_options/overview.html) library to bind environment variables. All BX environment variables are prefixed with `BX_`. Currently environment variables are bound explicitly (i.e. bindings are not generated from metadata).

`BX_CONFIG` is the only bound environment variable. BX uses a Boost feature to tie the environment variable and the command line option of the same identity (i.e. `--config`). Command line options have precedence if both are set.