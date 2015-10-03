Decode a stealth address.
```sh
$ bx stealth-decode --help
```
```
Usage: bx stealth-decode [-h] [--config VALUE] [--format VALUE]          
[STEALTH_ADDRESS]                                                        

Info: Decode a stealth address.                                          

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

STEALTH_ADDRESS      The stealth payment address. If not specified the   
                     address is read from STDIN.
```
The stealth address standard is not finalized. The most recent revision aligns the `version` byte with that of standard payment addresses. Previously stealth addresses used the prefix `42` for mainnet and `43` for testnet.

See also [stealth-encode](bx-stealth-encode).
### Example 1
scan key is spend key, version 42 (previous standard)
```sh
$ bx stealth-decode hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
```
```js
stealth_address
{
    encoded hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
    filter ""
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    }
    version 42
}
```
### Example 2
scan key and redundant spend key
```sh
$ bx stealth-decode 1DsiaW2kjjZAT92tAW8rvS1tF9ZSVzpz5WPBLAQFrPrMRMQQz7X6qR8h
```
```js
stealth_address
{
    encoded 1DsiaW2kjjZAT92tAW8rvS1tF9ZSVzpz5WPBLAQFrPrMRMQQz7X6qR8h
    filter ""
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    }
    version 0
}
```
### Example 3
scan key and additional spend key
```sh
$ bx stealth-decode 1Ht5EmHdUNVvRyMdJCwTZdBowDnbNJu8kaaZbkn4D4p7HTrppupQzETxVMdguNviAyEFj7e7mqKkqTncNeLdAv81Mm8jf9bzn7hBP
```
```js
stealth_address
{
    encoded 1Ht5EmHdUNVvRyMdJCwTZdBowDnbNJu8kaaZbkn4D4p7HTrppupQzETxVMdguNviAyEFj7e7mqKkqTncNeLdAv81Mm8jf9bzn7hBP
    filter ""
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 2
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
        public_key 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
    }
    version 0
}
```
### Example 3
one of two signatures required
```sh
$ bx stealth-decode vK4cs6xzzf326HyUeoJCQng6FXLVK27PyJoRbYSMyT9TzgKds8JDerKaRQ72q9kEp2tQNE2KRvabvqH5n5Rv6yv6Yht9uWN7nyPnY7
```
```js
stealth_address
{
    encoded vK4cs6xzzf326HyUeoJCQng6FXLVK27PyJoRbYSMyT9TzgKds8JDerKaRQ72q9kEp2tQNE2KRvabvqH5n5Rv6yv6Yht9uWN7nyPnY7
    prefix ""
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
        public_key 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
    }
    testnet false
}
```
### Example 4
maximum length prefix
```sh
$ bx stealth-decode 5b4Xkx9DVQj5nznykpKLeoNWHes1ZHJh3aCvxNNXUTuErKTyYq8NL8qVKcWGX4L
```
```js
stealth_address
{
    encoded 5b4Xkx9DVQj5nznykpKLeoNWHes1ZHJh3aCvxNNXUTuErKTyYq8NL8qVKcWGX4L
    prefix 11111111110000000000111111111100
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    }
    testnet false
}
```
### Example 5
prefix and one of two signatures required
```sh
$ bx stealth-decode JubEFUfmd2J3i83L9qWNr7fDSbb2bE7PY6RvEzH6wsNW8Ls7Mw3hxKZHWr3SvEz4o6NWLguFmyK9yBPrzxtC7ssTXQKJnyMUpFSHGvBua
```
```js
stealth_address
{
    encoded JubEFUfmd2J3i83L9qWNr7fDSbb2bE7PY6RvEzH6wsNW8Ls7Mw3hxKZHWr3SvEz4o6NWLguFmyK9yBPrzxtC7ssTXQKJnyMUpFSHGvBua
    prefix 000000001010
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
        public_key 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
    }
    testnet false
}
```
### Example 6
--format json, piped input
```sh
$ echo hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i | bx stealth-decode -f json
```
```js
{
    "stealth_address": {
        "encoded": "hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i",
        "prefix": "",
        "scan_public_key": "031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006",
        "signatures": "1",
        "spend": {
            "public_key": "031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006"
        },
        "testnet": "false"
    }
}
```