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
### Example 1
```sh
bx hd-to-ec xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
```
e8f32e723decf4051aefac8e2c93c9c5b214313817cdb01a1494b917c8436b35
```