Create a BIP16 pay-to-script-hash address from a script.
```sh
$ bx script-to-address --help
```
```
Usage: bx script-to-address [-h] [--config VALUE] [SCRIPT]               

Info: Create a BIP16 pay-to-script-hash address from a script.           

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SCRIPT               The script to use in the address. Multiple tokens   
                     must be quoted. If not specified the script is read 
                     from STDIN.
```
### Example 1
```sh
$ bx script-to-address dup hash160 [ 89abcdefabbaabbaabbaabbaabbaabbaabbaabba ] equalverify checksig
```
```
3F6i6kwkevjR7AsAd4te2YB2zZyASEm1HM
```