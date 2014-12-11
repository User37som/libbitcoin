#### Streams
Command implementations are provided with two invocation arguments, an output stream and an error stream. In BX command line processing these are populated by [STDOUT](http://wikipedia.org/wiki/Standard_streams#Standard_output_.28stdout.29) and [STDERR](http://wikipedia.org/wiki/Standard_streams#Standard_error_.28stderr.29) respectively. These values are mocked for unit testing.

#### Return Codes
Commands also return an enumerated integer value which is passed directly to the console upon command completion. The set of defined return codes is:

|value |meaning        |
|------|---------------|
|  -1  |failure        |
|   0  |success or true|
|   1  |false          |

#### Error Stream
The error stream is intended for human consumption, it is localized and not schematized. Programmatic interpretation of the failure condition, as well as `true` vs. `false` as applicable, should rely solely on the return code. It is possible for a command to fail and not write to the error stream and for a command to write warnings to the error stream in the case of successful execution.

#### Output Stream
Many commands return values encoded in the wire serialization defined by the [Bitcoin protocol](https://en.bitcoin.it/wiki/Protocol_specification). Typically this is either the [Base 10](http://en.wikipedia.org/wiki/Decimal), [Base 16](http://en.wikipedia.org/wiki/Hexadecimal), [Base 58](http://en.wikipedia.org/wiki/Base58) or [Base 64](http://en.wikipedia.org/wiki/Base64) standard [binary-to-text](http://en.wikipedia.org/wiki/Binary-to-text_encoding) encoding. This is referred to as **native** encoding.

Many commands that return complex objects support serializations to **xml**, **json** and **info** as defined by Boost's [property_tree](http://www.boost.org/doc/libs/1_41_0/doc/html/boost_propertytree/parsers.html). The default format is always **info**. The info and json formats escape values according to the [JSON standard](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf).

Commands with complex outputs define the `format` option:
```xml
<command symbol="address-decode" category="WALLET">
    <option name="help" description="Convert a Bitcoin address to RIPEMD160, dropping the version." />
    <option name="format" type="encoding" description="The output format. Options are 'json', 'xml', 'info' or 'native', defaults to 'info'." />
    <argument name="BITCOIN_ADDRESS" stdin="true" type="address" description="The Bitcoin address to convert. If not specified the address is read from STDIN."/>
</command>
```
To specify a non-default format set the `--format` option on the command line:
```sh
$ bx address-decode --format info 1HT7xU2Ngenf7D4yocz2SAcnNLW7rK8d4E
wrapper
{
    checksum 1476364070
    payload b472a266d0bd89c13706a4132ccfb16f7c3b9fcb
    version 0
}
```
> Outputs from certain commands can be passed directly into others. However, commands that accept complex types as arguments require **native** encoding.

#### Whitespace
As a matter of convention content written to either stream is terminated with the Line Feed character `0x0a`. However this presents no difficulty for input processing as [whitespace](http://en.wikipedia.org/wiki/Whitespace_character), including the Line Feed character, is ignored except as a delimiter.

#### Cardinality
Some commands can return more than one instance of a given type. In such cases individual instances are separated by the Line Feed character `0x0a`.