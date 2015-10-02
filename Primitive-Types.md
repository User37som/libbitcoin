BX uses the following set of types for command and configuration processing.
```
bc::config::authority
bc::config::btc256
bc::config::checkpoint
bc::config::endpoint

bc::wallet::bicoin_uri
bc::wallet::ec_private
bc::wallet::ec_public
bc::wallet::ek_private
bc::wallet::ek_public
bc::wallet::ek_token
bc::wallet::hd_private
bc::wallet::hd_public
bc::wallet::payment_address
bc::wallet::stealth_address

bc::explorer::primitives::base16
bc::explorer::primitives::base2
bc::explorer::primitives::base58
bc::explorer::primitives::base64
bc::explorer::primitives::base85
bc::explorer::primitives::btc
bc::explorer::primitives::btc160
bc::explorer::primitives::byte
bc::explorer::primitives::cert_key
bc::explorer::primitives::ec_private
bc::explorer::primitives::ec_public
bc::explorer::primitives::encoding
bc::explorer::primitives::endorsement
bc::explorer::primitives::hashtype
bc::explorer::primitives::hd_key
bc::explorer::primitives::header
bc::explorer::primitives::input
bc::explorer::primitives::language
bc::explorer::primitives::output
bc::explorer::primitives::point
bc::explorer::primitives::raw
bc::explorer::primitives::script
bc::explorer::primitives::signature
bc::explorer::primitives::transaction
bc::explorer::primitives::wrapper
```
These are individual classes that are for the most part simple wrappers around types and/or functions exposed by [libbitcoin](https://github.com/libbitcoin/libbitcoin). The classes consistently implement overrides of stream operators by conversion to/from text encodings. As a result they drop seamlessly into [input processing](Input-Processing) and [output processing](Output-Processing) like any other serializable type.

Deserialization by any of these primitives, including string-based construction, can throw `boost::program_options::invalid_option_value`. One should consider handling this exception when using `libbitcoin-explorer` as a library.

The primitives that represent complex types also provide conversion functions to Boost [property_tree](http://www.boost.org/doc/libs/1_50_0/doc/html/property_tree.html), enabling complex textual serializations in addition to native formats. BX does not currently support complex textual deserializations apart from native formats, although that could be accomplished in part by extending the primitives with property\_tree deserialization.