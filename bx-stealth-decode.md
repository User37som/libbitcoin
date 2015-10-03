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
### Example 4
one of two signatures required
```sh
$ bx stealth-decode 1Ht5EmHdUNVvRyMdJCwTZdBowDnbNJu8kaaZbkn4D4p7HTrppupQzETxVMdguNviAyEFj7e7mqKkqTncNeLdAv81Mm8jf978insV8
```
```js
stealth_address
{
    encoded 1Ht5EmHdUNVvRyMdJCwTZdBowDnbNJu8kaaZbkn4D4p7HTrppupQzETxVMdguNviAyEFj7e7mqKkqTncNeLdAv81Mm8jf978insV8
    filter ""
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
        public_key 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
    }
    version 0
}
```
### Example 5
maximum length prefix
```sh
$ bx stealth-decode 12TFFcDyvpZd4Zy1GAS7sp7Xz9sgRabovgf8xfD4EMGxenJw8ivsa3bBj8TzjR
```
```js
stealth_address
{
    encoded 12TFFcDyvpZd4Zy1GAS7sp7Xz9sgRabovgf8xfD4EMGxenJw8ivsa3bBj8TzjR
    filter 11111111110000000000111111111100
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    }
    version 0
}
```
### Example 6
prefix and one of two signatures required
```sh
$ bx stealth-decode 16frt2rsvRjxyyqExjiRAkmm6g8NPRnFURWCZosVnPrSYBK9sM8j74PPGDd2MtiZuSPoLzVTgQ1P5k9Xm2ExkMhFqVTQfZ8jFEqkNomZ
```
```js
stealth_address
{
    encoded 16frt2rsvRjxyyqExjiRAkmm6g8NPRnFURWCZosVnPrSYBK9sM8j74PPGDd2MtiZuSPoLzVTgQ1P5k9Xm2ExkMhFqVTQfZ8jFEqkNomZ
    filter 000000001010
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
        public_key 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
    }
    version 0
}
```
### Example 7
version 111 (testnet)
```sh
$ bx stealth-decode 2rT9GaRuU7hM5DiaP6FDbRWX9tLuh5E5QC6mG6jVfMSm7LHmiGFbDhHfHe
```
```js
stealth_address
{
    encoded 2rT9GaRuU7hM5DiaP6FDbRWX9tLuh5E5QC6mG6jVfMSm7LHmiGFbDhHfHe
    filter ""
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    }
    version 111
}
```
### Example 8
--format json, piped input
```sh
$ echo hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i | bx stealth-decode -f json
```
```js
{
    "stealth_address": {
        "encoded": "hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i",
        "filter": "",
        "scan_public_key": "031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006",
        "signatures": "1",
        "spend": {
            "public_key": "031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006"
        },
        "version": "42"
    }
}
```