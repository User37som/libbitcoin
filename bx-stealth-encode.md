Encode a stealth payment address. 
```sh
$ bx stealth-encode --help
```
```
Usage: bx stealth-encode [-h] [--config VALUE] [--prefix VALUE]          
[--signatures VALUE] [--version VALUE] SCAN_PUBKEY [SPEND_PUBKEY]...     

Info: Encode a stealth payment address.                                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-p [--prefix]        The Base2 stealth prefix that will be used to locate
                     payments.                                           
-s [--signatures]    The number of signatures required to spend a payment
                     to the stealth address. Defaults to the number of   
                     SPEND_PUBKEYs.                                      
-v [--version]       The desired payment address version, defaults to 0. 

Arguments (positional):

SCAN_PUBKEY          The Base16 EC public key required to create a       
                     payment.                                            
SPEND_PUBKEY         The set of Base16 EC public keys corresponding to   
                     private keys that will be able to spend payments to 
                     the address. Defaults to the value of SCAN_PUBKEY.
```
The stealth address standard is not finalized. The most recent revision aligns the `version` byte with that of standard payment addresses. Previously stealth addresses used the prefix `42` for mainnet and `43` for testnet.

See also [stealth-decode](bx-stealth-decode).
### Example 1
scan key only, --version 42 (previous standard)
```sh
$ bx stealth-encode -v 42 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
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
1DsiaW2kjjZAT92tAW8rvS1tF9ZSVzpz5WPBLAQFrPrMRMQQz7X6qR8h
```

> Notice that the stealth address remains unchanged when the only spend key is explicitly the same as the scan key.

### Example 3
scan key and additional spend key
```sh
$ bx stealth-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006  024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
WARNING: multiple signature stealth transactions are not yet fully supported.
1Ht5EmHdUNVvRyMdJCwTZdBowDnbNJu8kaaZbkn4D4p7HTrppupQzETxVMdguNviAyEFj7e7mqKkqTncNeLdAv81Mm8jf9bzn7hBP
```

> In this case the scan key is specified as a spend key along with a second spend key. As in this case, if additional spend keys are specified and the scan key is to be a spend key as well, the scan key must be explicitly specified.

> [tx-encode](bx-tx-encode) does not yet support creation of multiple signature stealth transactions.

> By default signature by all spend keys is required to spend payments to the address. The warning message is written to STDERR although the command returns success.

### Example 4
one of two signatures required, --signatures 1
```sh
$ bx stealth-encode -s 1 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006  024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
WARNING: multiple signature stealth transactions are not yet fully supported.
1Ht5EmHdUNVvRyMdJCwTZdBowDnbNJu8kaaZbkn4D4p7HTrppupQzETxVMdguNviAyEFj7e7mqKkqTncNeLdAv81Mm8jf978insV8
```

> Notice the address differs from the previous example because the signature requirement has been altered.

### Example 5
signature overflow error, --signatures 42
```sh
$ bx stealth-encode -s 42 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006  024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
The number of signatures is greater than the number of SPEND_PUBKEYs.
```
### Example 6
--prefix 11111111110000000000111111111100
```sh
$ bx stealth-encode -p 11111111110000000000111111111100 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
12TFFcDyvpZd4Zy1GAS7sp7Xz9sgRabovgf8xfD4EMGxenJw8ivsa3bBj8TzjR
```

> This example shows the maximum length prefix of 32 bits. Generally speaking the privacy afforded by stealth transactions is reduced as the search prefix increases in length. The prefix is a transaction search optimization for the recipient. The most private stealth transactions would not use a prefix.

### Example 7
--prefix 000000001010 --signatures 1
```sh
$ bx stealth-encode -p 000000001010 -s 1 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006  024c6988f8e64242a1b8f33513f5f27b9e135ad0a11433fc590816ff92a353a969
```
```
WARNING: multiple signature stealth transactions are not yet fully supported.
16frt2rsvRjxyyqExjiRAkmm6g8NPRnFURWCZosVnPrSYBK9sM8j74PPGDd2MtiZuSPoLzVTgQ1P5k9Xm2ExkMhFqVTQfZ8jFEqkNomZ
```
### Example 8
--version 111 (testnet)
```sh
$ bx stealth-encode -v 111 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
2rT9GaRuU7hM5DiaP6FDbRWX9tLuh5E5QC6mG6jVfMSm7LHmiGFbDhHfHe
```