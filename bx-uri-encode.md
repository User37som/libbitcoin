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
[BIP-21 Examples](https://github.com/bitcoin/bips/blob/master/bip-0021.mediawiki#Examples) address
```sh
$ bx uri-encode 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
```
```
bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
```
### Example 2
[BIP-21 Examples](https://github.com/bitcoin/bips/blob/master/bip-0021.mediawiki#Examples) address, --label
```sh
$ bx uri-encode -l Luke-Jr 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
```
```
bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?label=Luke-Jr
```
### Example 3
[BIP-21 Examples](https://github.com/bitcoin/bips/blob/master/bip-0021.mediawiki#Examples) address, --amount, --label
```sh
$ bx uri-encode -a 20.3 -l Luke-Jr 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
```
```
bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?amount=20.3&label=Luke-Jr
```
### Example 4
[BIP-21 Examples](https://github.com/bitcoin/bips/blob/master/bip-0021.mediawiki#Examples) address, --amount, --label, --message
```sh
$ bx uri-encode -a 20.3 -l Luke-Jr -m "Donation for project xyz" 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
```
```
bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?amount=20.3&label=Luke-Jr&message=Donation%20for%20project%20xyz
```
### Example 5
stealth address
```sh
$ bx uri-encode -s hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
```
```
bitcoin:hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
```