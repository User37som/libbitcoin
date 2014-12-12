Convert a Base64 value to binary data. 
```sh
$ bx base64-decode --help
```
```
Usage: bx base64-decode [-h] [--config VALUE] [BASE64]                   

Info: Convert a Base64 value to binary data.                             

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE64               The Base64 value to decode as binary data. If not   
                     specified the value is read from STDIN.
```
See also [base64-encode](bx-base64-encode).
### Example 1
```sh
$ bx base64-decode TGV0IHVzIHNwZWFrIG5vIG1vcmUgb2YgZmFpdGggaW4gbWFuLCBidXQgYmluZCBoaW0gZG93biBmcm9tIG1pc2NoaWVmIGJ5IHRoZSBjaGFpbnMgb2YgY3J5cHRvZ3JhcGh5Lg==
```
```
Let us speak no more of faith in man, but bind him down from mischief by the chains of cryptography.
```