Convert a HD (BIP32) public or private key to the equivalent EC    
public or private key.
```sh
$ bx hd-to-ec --help
```
```
Usage: bx hd-to-ec [-h] [--config VALUE] [HD_KEY]                        

Info: Convert a HD (BIP32) public or private key to the equivalent EC    
public or private key.                                                   

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

HD_KEY               The HD public or private key to convert. If not     
                     specified the key is read from STDIN.
```