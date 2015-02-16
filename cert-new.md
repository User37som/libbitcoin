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
$ cat mycert
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
### Example 2
--metadata email:foo@bar.org --metadata phone:+1-603-555-1212
```sh
$ bx cert-new mycert --metadata email:foo@bar.org --metadata phone:+1-603-555-1212
$ cat mycert
```
```sh
#   ****  Generated on 2015-02-16 01:31:21 by CZMQ  ****
#   ZeroMQ CURVE **Secret** Certificate
#   DO NOT PROVIDE THIS FILE TO OTHER USERS nor change its permissions.

metadata
    phone = "+1-603-555-1212"
    email = "foo@bar.org"
curve
    public-key = "ke4jTqsF>?-[F>9PE29c2.us&-Hl)89K^wx]kx.a"
    secret-key = "?$-xHWL]zF7OF1rI-mR-!L%*w+%Ci<Wo8}Adt]F)"
```