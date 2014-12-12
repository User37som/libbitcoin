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
A valid signature proves ownership of the Bitcoin address used in validation. However it is important that the message used in verification be unpredictable to the signer and provided by the party requiring the validation. Otherwise the process is subject to a [replay attack](http://en.wikipedia.org/wiki/Replay_attack).

See also [message-sign](bx-message-sign).
### Example 1
```sh
$ bx message-validate 1BCyH5qVL5EkfhQnw4WmqfDDekJefKYEYj IPEb09fvqo/QMFq2kf8PC3cEcWs0C+7Kv8ImKNkUv3I3CvVwDzHkjgJHGYWnFhpbQRQJKQFd+Bww/1qUpNjh0J0= "Who is John Galt?"
```
```
The signature is valid.
```
### Example 2
routed input, validate self
```sh
$ bx message-validate 1BCyH5qVL5EkfhQnw4WmqfDDekJefKYEYj II/InhNcMd4PlrEkpp7sJTeR42okpc4b/JgojxnMib7lSNvTicnSahDxuOjZbO3WJWRdocUa3UtyrW1YEIh3wDY= < bx.exe
```
```
The signature is valid.
```