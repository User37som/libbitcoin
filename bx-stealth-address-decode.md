Decode a stealth address.
```sh
$ bx stealth-address-decode --help
```
```
Usage: bx stealth-address-decode [-h] [--config VALUE] [--format VALUE]  
STEALTH_ADDRESS                                                          

Info: Decode a stealth address.                                          

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

STEALTH_ADDRESS      The stealth payment address.
```
### Example 1
scan key is spend key
```sh
$ bx stealth-address-decode hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
```
```js
stealth_address
{
    encoded hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
    prefix ""
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    }
    testnet false
}
```
### Example 2
scan key and additional spend key
```sh
$ bx stealth-address-decode vK4cs6xzzf326HyUeoJCQng6FXLVK27PyJoRbYSMyT9TzgKds8JDerKaRQ72q9kEp2tQNE2KRvabvqH5n5Rv6yv6Yht9uWNcbDGD7d
```
```js
stealth_address
{
    encoded vK4cs6xzzf326HyUeoJCQng6FXLVK27PyJoRbYSMyT9TzgKds8JDerKaRQ72q9kEp2tQNE2KRvabvqH5n5Rv6yv6Yht9uWNcbDGD7d
    prefix ""
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 2
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
        public_key 024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
    }
    testnet false
}
```
### Example 3
one of two signatures required
```sh
$ bx stealth-address-decode vK4cs6xzzf326HyUeoJCQng6FXLVK27PyJoRbYSMyT9TzgKds8JDerKaRQ72q9kEp2tQNE2KRvabvqH5n5Rv6yv6Yht9uWN7nyPnY7
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
prefix 11111111110000000000111111111100
```sh
bx stealth-address-decode 5b4Xkx9DVQj5nznykpKLeoNWHes1ZHJh3aCvxNNXUTuErKTyYq8NKX3xNb3Q7xg
```
```js
stealth_address
{
    encoded 5b4Xkx9DVQj5nznykpKLeoNWHes1ZHJh3aCvxNNXUTuErKTyYq8NKX3xNb3Q7xg
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