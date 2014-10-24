Decode a script to plain text tokens.
```sh
$ bx script-decode --help
```
```
Usage: bx script-decode [-h] [--config VALUE] [SCRIPT]                   

Info: Decode a script to plain text tokens.                              

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SCRIPT               The Base16 script. If not specified the script is   
                     read from STDIN.
```
This command is helpful in interpreting scripts as they appear in the wire protocol. It is not used in conjunction with other commands apart from `script-encode`.

See also [script-encode](bx-script-encode).
### Example 1
[Bitcoin Wiki script example](https://en.bitcoin.it/wiki/Script#Scripts)
```sh
$ bx script-decode 76A91489ABCDEFABBAABBAABBAABBAABBAABBAABBAABBA88AC
```
```
dup hash160 [ 89abcdefabbaabbaabbaabbaabbaabbaabbaabba ] equalverify checksig
```