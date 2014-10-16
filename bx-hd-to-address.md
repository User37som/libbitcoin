Convert a HD (BIP32) public or private key to a Bitcoin address.   
```sh
$ bx hd-to-address --help
```
```
Usage: bx hd-to-address [-h] [--config VALUE] [HD_KEY]                   

Info: Convert a HD (BIP32) public or private key to a Bitcoin address.   

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

HD_KEY               The HD public or private key to convert. If not     
                     specified the key is read from STDIN.   
```
### Example 1
private key
```sh
$ bx hd-to-address xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
```
15mKKb2eos1hWa6tisdPwwDC1a5J1y9nma
```
### Example 2
public key
```sh
$ bx hd-to-address xpub661MyMwAqRbcFtXgS5sYJABqqG9YLmC4Q1Rdap9gSE8NqtwybGhePY2gZ29ESFjqJoCu1Rupje8YtGqsefD265TMg7usUDFdp6W1EGMcet8
```
```
15mKKb2eos1hWa6tisdPwwDC1a5J1y9nma
```