BX uses the following set of types for command and configuration processing.
```
bc::config::authority
bc::config::base2
bc::config::base16
bc::config::base58
bc::config::base64
bc::config::checkpoint
bc::config::endpoint
bc::config::hash160
bc::config::hash256
bc::config::sodium

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

bc::explorer::config::address
bc::explorer::config::algorithm
bc::explorer::config::btc
bc::explorer::config::byte
bc::explorer::config::cert_key
bc::explorer::config::ec_private
bc::explorer::config::ec_public
bc::explorer::config::encoding
bc::explorer::config::endorsement
bc::explorer::config::hashtype
bc::explorer::config::hd_key
bc::explorer::config::header
bc::explorer::config::input
bc::explorer::config::language
bc::explorer::config::output
bc::explorer::config::point
bc::explorer::config::raw
bc::explorer::config::script
bc::explorer::config::signature
bc::explorer::config::transaction
bc::explorer::config::wrapper
```
These are individual classes that are for the most part simple wrappers around types and/or functions exposed by [libbitcoin](https://github.com/libbitcoin/libbitcoin). The classes consistently implement overrides of stream operators by conversion to/from text encodings. As a result they drop seamlessly into [input processing](Input-Processing) and [output processing](Output-Processing) like any other serializable type.

Deserialization by any of these primitives, including string-based construction, can throw `boost::program_options::invalid_option_value`. One should consider handling this exception when using `libbitcoin-explorer` as a library.

The primitives that represent complex types also provide conversion functions to Boost [property_tree](http://www.boost.org/doc/libs/1_50_0/doc/html/property_tree.html), enabling complex textual serializations in addition to native formats. BX does not currently support complex textual deserializations apart from native formats, although that could be accomplished in part by extending the primitives with property\_tree deserialization.