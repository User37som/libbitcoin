Validate a message signature.
```sh
$ bx message-validate --help
```
```
Usage: bx message-validate [-h] [--config VALUE] BITCOIN_ADDRESS         
SIGNATURE [MESSAGE]                                                      

Info: Validate a message signature.                                      

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BITCOIN_ADDRESS      The Bitcoin address of the message signer.          
SIGNATURE            The message signature.                              
MESSAGE              The binary message data for which the signature     
                     applies. If not specified the message is read from  
                     STDIN.
```
A valid signature proves ownership of the Bitcoin address used in validation. However it is important that the message used in verification be unpredictable to the signer and provided by the party requiring the validation. Otherwise the process becomes subject to a [replay attack](http://en.wikipedia.org/wiki/Replay_attack).

See also [message-sign](bx-message-sign).
### Example 1
```sh
$ bx message-validate 1BCyH5qVL5EkfhQnw4WmqfDDekJefKYEYj INjouW95WM+sbzZ5z2rN/DBDpDwNuEWJ2xQqA+G3zm3MRDFUNPwImCSSX3dHQscxic0id+cxxiQjxEoRTDAuaPU= "Let us speak no more of faith in man, but bind him down from mischief by the chains of cryptography."
```
```
The signature is valid.
```