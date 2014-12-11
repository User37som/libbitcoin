Validate a message signature.
```sh
$bx message-validate --help
```
```
Usage: bx message-validate [-h] [--config VALUE] [BITCOIN_ADDRESS]       
[SIGNATURE] [MESSAGE]                                                    

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