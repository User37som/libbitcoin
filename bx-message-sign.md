Create a message signature.
```sh
$ bx message-sign --help
```
```
Usage: bx message-sign [-h] [--config VALUE] WIF [MESSAGE]               

Info: Create a message signature.                                        

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

WIF                  The WIF private key to use for signing.             
MESSAGE              The binary message data to sign. If not specified   
                     the message is read from STDIN.
```
See also [message-validate](bx-message-validate).
### Example 1
```sh
$ bx message-sign L13gvvM3TtL2EmfBdye8tp4tQhcbCG3xz3VPrBjSZL8MeJavLL8K "Let us speak no more of faith in man, but bind him down from mischief by the chains of cryptography."
```
```
INjouW95WM+sbzZ5z2rN/DBDpDwNuEWJ2xQqA+G3zm3MRDFUNPwImCSSX3dHQscxic0id+cxxiQjxEoRTDAuaPU=
```