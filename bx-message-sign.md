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