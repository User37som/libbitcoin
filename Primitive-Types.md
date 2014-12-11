### Primitive Types
BX defines the following set of Bitcoin primitive types in the `bx::primitives` namespace.
```
address
base2
base10
base16
base58
base64
btc160
btc256
ec_private
ec_public
encoding
endorsement
hashtype
hd_key
hd_priv
hd_pub
header
input
output
point
raw
script
signature
stealth
transaction
uri
wif
wrapper
```
These are individual classes that are for the most part simple wrappers around types and/or functions exposed by [libbitcoin](https://github.com/libbitcoin/libbitcoin). The classes consistently implement overrides of stream operators by conversion to/from text encodings. As a result they drop seamlessly into [input processing](Input-Processing) and [output processing](Output-Processing) like any other serializable type.

Deserialization by any of these primitives, including string-based construction, can throw `boost::program_options::invalid_option_value`. One should consider handling this exception when using `libbitcoin-explorer` as a library.

The primitives that represent complex types also provide conversion functions to Boost [property_tree](http://www.boost.org/doc/libs/1_50_0/doc/html/property_tree.html), enabling complex textual serializations in addition to native formats. BX does not currently support complex textual deserializations apart from native formats, although that could be accomplished in part by extending the primitives with property\_tree deserialization.