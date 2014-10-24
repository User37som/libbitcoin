Encode a stealth payment address. 
```sh
$ bx stealth-encode --help
```
```
Usage: bx stealth-encode [-h] [--config VALUE] [--prefix VALUE]          
[--signatures VALUE] SCAN_PUBKEY [SPEND_PUBKEY]...                       

Info: Encode a stealth payment address.                                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-p [--prefix]        The Base2 stealth prefix that will be used to locate
                     payments.                                           
-s [--signatures]    Specify the number of signatures required to spend a
                     payment to the stealth address. Defaults to the     
                     number of SPEND_PUBKEYs.                            

Arguments (positional):

SCAN_PUBKEY          The Base16 EC public key required to generate a     
                     payment.                                            
SPEND_PUBKEY         The set of Base16 EC public keys corresponding to   
                     private keys that will be able to spend payments to 
                     the address. Defaults to the value of SCAN_PUBKEY.  
```
See also [stealth-decode](bx-stealth-decode).
### Example 1
scan key only
```sh
$ bx stealth-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
```

> This is the simplest address, as the only spend key is the same as the scan key.

### Example 2
scan key and redundant spend key
```sh
$ bx stealth-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
```

> Notice that the stealth address remains unchanged when the only spend key is explicitly the same as the scan key.

### Example 3
scan key and additional spend key
```sh
$ bx stealth-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006  024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
WARNING: multiple signature stealth transactions are not yet fully supported.
vK4cs6xzzf326HyUeoJCQng6FXLVK27PyJoRbYSMyT9TzgKds8JDerKaRQ72q9kEp2tQNE2KRvabvqH5n5Rv6yv6Yht9uWNcbDGD7d
```

> In this case the scan key is specified as a spend key along with a second spend key. As in this case, if additional spend keys are specified and the scan key is to be a spend key as well, the scan key must be explicitly specified.

> Obelisk does not yet support discovery of multiple signature stealth transactions.

> By default signature by all spend keys is required to spend payments to the address. The warning message is written to STDERR although the command returns success.

### Example 4
--signatures 1, one of two signatures required
```sh
$ bx stealth-encode -s 1 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006  024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
WARNING: multiple signature stealth transactions are not yet fully supported.
vK4cs6xzzf326HyUeoJCQng6FXLVK27PyJoRbYSMyT9TzgKds8JDerKaRQ72q9kEp2tQNE2KRvabvqH5n5Rv6yv6Yht9uWN7nyPnY7
```

> Notice the address differs from the previous example because the signature requirement has been altered.

### Example 5
--signatures 42, signature overflow error
```sh
$ bx stealth-encode -s 42 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006  024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
The number of signatures is greater than the number of SPEND_PUBKEYs.
```
### Example 6
--prefix 11111111110000000000111111111100
```sh
$ bx stealth-address-encode -p 11111111110000000000111111111100 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
5b4Xkx9DVQj5nznykpKLeoNWHes1ZHJh3aCvxNNXUTuErKTyYq8NKX3xNb3Q7xg
```

> This example shows the maximum length prefix of 32 bits. Generally speaking the privacy afforded by stealth transactions is reduced as the search prefix increases in length. The prefix is a transaction search optimization for the recipient. The most private stealth transactions would not use a prefix.

### Example 7
--prefix 000000001010, --signatures 1
```sh
$ bx stealth-encode -p 000000001010 -s 1 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006  024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
WARNING: multiple signature stealth transactions are not yet fully supported.
JubEFUfmd2J3i83L9qWNr7fDSbb2bE7PY6RvEzH6wsNW8Ls7Mw3hxKZHWr3SvEz4o6NWLguFmyK9yBPrzxtC7ssTXQKJnyMUpL71mzBgd
```