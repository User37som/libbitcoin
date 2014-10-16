Convert a HD (BIP32) private key to a WIF private key.  
```sh
$ bx hd-to-wif --help
```
```
Usage: bx hd-to-wif [-h] [--config VALUE] [HD_PRIVATE_KEY]               

Info: Convert a HD (BIP32) private key to a WIF private key.             

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

HD_PRIVATE_KEY       The HD private key to convert. If not specified the 
                     key is read from STDIN.
```
### Example 1
```sh
$ bx hd-to-wif xprv9s21ZrQH143K27rVid1zpeyqZygAX7W7AQ4cctwrSB4A2EoPNT22nR2FCm42oc6UmTNGnjwLscDdkof6dyRVwoG8nU6uY8XTGNHiNzAx3TD
```
```
KxL385uvhm2PhgTjk6gvHPE81xNwCDd1WeQXPMR4DMZfVNJRSvwF
```
### Example 2
piped commands
```sh
$ bx seed | bx hd-new | bx hd-to-wif
```
```
6aaa7ddba5ab18231c7e4d40327a1c66
xprv9s21ZrQH143K2ZSgqjBCCxNPEUTQYsnmNAf8vH7jGtQHJoEUVvrRYTFWQbH9dAgWH73c1ut2jbNoxuzinaCpQPT6vSk6xkNJvi6mDm9yLkf
L3ouKDHFbLZwd4sWLnExpQzFE2HfKhtSMnt8QkPXLksDRWdonAvk
```