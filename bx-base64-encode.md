Convert binary data to Base64.
```sh
$ bx base64-encode --help
```
```
Usage: bx base64-encode [-h] [--config VALUE] [DATA]                     

Info: Convert binary data to Base64.                                     

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

DATA                 The binary data to encode as Base64. This can be    
                     text or any other data. If not specified the data is
                     read from STDIN.
```
### Example 1
```sh
$ bx base64-encode "Let us speak no more of faith in man, but bind him down from mischief by the chains of cryptography."
```
```
TGV0IHVzIHNwZWFrIG5vIG1vcmUgb2YgZmFpdGggaW4gbWFuLCBidXQgYmluZCBoaW0gZG93biBmcm9tIG1pc2NoaWVmIGJ5IHRoZSBjaGFpbnMgb2YgY3J5cHRvZ3JhcGh5Lg==
```