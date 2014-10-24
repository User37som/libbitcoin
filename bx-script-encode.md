Base16 encode a plain text script.
```sh
$ bx script-encode --help
```
```
Usage: bx script-encode [-h] [--config VALUE] [TOKEN]...                 

Info: Base16 encode a plain text script.                                 

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

TOKEN                The plain text script tokens that make up the       
                     script. If not specified the tokens are read from   
                     STDIN.
```
This command is helpful in interpreting scripts as they appear in the wire protocol. It is not used in conjunction with other commands apart from `script-decode`.

See also [script-decode](bx-script-decode).
### Example 1
[Bitcoin Wiki example](https://en.bitcoin.it/wiki/Script#Scripts)
```sh
$ bx script-encode dup hash160 [ 89abcdefabbaabbaabbaabbaabbaabbaabbaabba ] equalverify checksig
```
```
76a91489abcdefabbaabbaabbaabbaabbaabbaabbaabba88ac
```