```sh
$ bx cert-new --help
```
```
Usage: bx cert-new [-h] [--config VALUE] [--metadata VALUE] PRIVATE_CERT 

Info: Create a private Curve ZMQ certificate for use with a              
Libbitcoin/Obelisk server. WARNING: entropy is obtained from the         
underlying platform.                                                     

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-m [--metadata]      The set of name-value pairs to add as metadata to   
                     the certificate, encoded as NAME:VALUE.             

Arguments (positional):

PRIVATE_CERT         The path to write the certificate file.             
```
### Example 1
```sh
$ bx cert-new mycert
$ type mycert
```
```sh
#   ****  Generated on 2015-02-16 01:23:56 by CZMQ  ****
#   ZeroMQ CURVE **Secret** Certificate
#   DO NOT PROVIDE THIS FILE TO OTHER USERS nor change its permissions.

metadata
curve
    public-key = "7]g&M3GX##D.-!L>B.t?=@V6nkC34imk5/65kMNp"
    secret-key = "]k2&)P6O#/m5XE%RTFFsrkX&-gEH5]aPxjwBgE?O"
```