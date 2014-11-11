Compose a Bitcoin URI from specified parts. 
```sh
$ bx uri-encode --help
```
```
Usage: bx uri-encode [-h] [--amount VALUE] [--config VALUE] [--label     
VALUE] [--message VALUE] [--request VALUE] [--stealth VALUE]             
[BITCOIN_ADDRESS]                                                        

Info: Compose a Bitcoin URI from specified parts.                        

Options (named):

-a [--amount]        The value of the amount parameter.                  
-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-l [--label]         The value of the label parameter.                   
-m [--message]       The value of the label parameter.                   
-r [--request]       The value of the payment request parameter.         
-s [--stealth]       The stealth address for the address part.           

Arguments (positional):

BITCOIN_ADDRESS      The Bitcoin address for the address part.
```
See also [uri-decode](bx-uri-decode).
### Example 1
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) Bitcoin address
```sh
$ bx uri-encode 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
```
```
bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
```
### Example 2
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) address and label
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?label=Luke-Jr"
```
```

```
### Example 3
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) address, amount and label
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?amount=20.3&label=Luke-Jr"
```
```

```
### Example 4
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) address, amount, label and message
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?amount=50&label=Luke-Jr&message=Donation%20for%20project%20xyz"
```
```

```
### Example 5
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) required but unknown parameters
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?req-somethingyoudontunderstand=50&req-somethingelseyoudontget=999"
```
```

```
### Example 6
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) optional unknown parameters
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?somethingyoudontunderstand=50&somethingelseyoudontget=999"
```
```

```
### Example 7
stealth address
```sh
$ bx uri-decode "bitcoin:hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i"
```
```

```
### Example 8
piped command
```sh
$ echo bitcoin:hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i?amount=99999999.99999999 | bx uri-decode
```
> Notice that the echo'd value is not quoted.

```

```