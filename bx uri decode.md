Validate and decompose a Bitcoin URI into its parts. 
```sh
$ bx uri-decode --help
```
```
Usage: bx uri-decode [-h] [--config VALUE] [--format VALUE] [URI]        

Info: Validate and decompose a Bitcoin URI into its parts.               

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

URI                  The Bitcoin URI to decode. The URI should be quoted 
                     when entered on the command line. If not specified  
                     the URI is read from STDIN.   
```
See also [uri-decode](bx-uri-encode).
### Example 1
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) Bitcoin address
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L"
```
```js
uri
{
    address 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
    scheme bitcoin
}
```
### Example 2
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) address and label
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?label=Luke-Jr"
```
```js
uri
{
    address 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
    label Luke-Jr
    scheme bitcoin
}
```
### Example 3
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) address, amount and label
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?amount=20.3&label=Luke-Jr"
```
```js
uri
{
    address 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
    amount 2030000000
    scheme bitcoin
}
```
### Example 4
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) address, amount, label and message
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?amount=50&label=Luke-Jr&message=Donation%20for%20project%20xyz"
```
```js
uri
{
    address 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
    amount 5000000000
    label Luke-Jr
    message "Donation for project xyz"
    scheme bitcoin
}
```
### Example 5
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) required but unknown parameters
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?req-somethingyoudontunderstand=50&req-somethingelseyoudontget=999"
```
```
Error: the argument ('bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?req-somethingyoudontunderstand=50') for option URI is invalid
```
### Example 6
[BIP-21 Examples](https://github.com/evoskuil/bips/blob/master/bip-0021.mediawiki#Examples) optional unknown parameters
```sh
$ bx uri-decode "bitcoin:1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L?somethingyoudontunderstand=50&somethingelseyoudontget=999"
```
```js
uri
{
    address 1NS17iag9jJgTHD1VXjvLCEnZuQ3rJED9L
    scheme bitcoin
}
```
### Example 7
stealth address
```sh
$ bx uri-decode "bitcoin:hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i"
```
```js
uri
{
    address hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
    scheme bitcoin
}
```
### Example 8
piped command
```sh
$ echo bitcoin:hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i?amount=99999999.99999999 | bx uri-decode
```
> Notice that the echo'd value is not quoted.

```js
uri
{
    address hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
    amount 9999999999999999
    scheme bitcoin
}
```