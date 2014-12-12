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
By signing data provided by another party the signer can prove to that party ownership of a Bitcoin address. This can be carried out over a public network and does not risk compromise of the private key of the address.

The WIF key used in signing must correspond to the Bitcoin address for which validation is required. Otherwise subsequent validation against that address will fail. WIF keys contain a flag indicating whether the corresponding Bitcoin address is derived from the corresponding EC public key in the compressed or the uncompressed format.

See also [message-validate](bx-message-validate).
### Example 1
```sh
$ bx message-sign L13gvvM3TtL2EmfBdye8tp4tQhcbCG3xz3VPrBjSZL8MeJavLL8K "Let us speak no more of faith in man, but bind him down from mischief by the chains of cryptography."
```
```
INjouW95WM+sbzZ5z2rN/DBDpDwNuEWJ2xQqA+G3zm3MRDFUNPwImCSSX3dHQscxic0id+cxxiQjxEoRTDAuaPU=
```
### Example 2
routed input, sign self
```sh
$ bx message-sign L13gvvM3TtL2EmfBdye8tp4tQhcbCG3xz3VPrBjSZL8MeJavLL8K < bx.exe
```
```
II/InhNcMd4PlrEkpp7sJTeR42okpc4b/JgojxnMib7lSNvTicnSahDxuOjZbO3WJWRdocUa3UtyrW1YEIh3wDY=
```