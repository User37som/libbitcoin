Create a derived public Curve ZMQ certificate for use with a       
Libbitcoin/Obelisk server. 
```sh
$ bx cert-public --help
```
```
Usage: bx cert-public [-h] [--config VALUE] [--metadata VALUE]           
PRIVATE_CERT PUBLIC_CERT                                                 

Info: Create a derived public Curve ZMQ certificate for use with a       
Libbitcoin/Obelisk server.                                               

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-m [--metadata]      The set of name-value pairs to add as metadata to   
                     the new certificate, encoded as NAME:VALUE.         

Arguments (positional):

PRIVATE_CERT         The path to read the private certificate file.      
PUBLIC_CERT          The path to write the public certificate file.      
```
Certificates are only written to a file path. If a file already exists in the path an error will result. The format of the certificate file is [ZeroMQ Property Language (ZPL)](http://rfc.zeromq.org/spec:4).

Public certificates are consumed directly by [Libbitcoin Server](https://github.com/libbitcoin/libbitcoin-server) for client identity.

BX does not use a full certificate for server identity, instead using the unquoted value of the server certificate's `public-key` property.

See also [cert-new](bx-cert-new).
### Example 1
```sh
$ bx cert-public my_private_cert1 my_public_cert1
```
```sh
$ cat my_public_cert1
#   ****  Generated on 2015-02-16 01:58:16 by CZMQ  ****
#   ZeroMQ CURVE Public Certificate
#   Exchange securely, or use a secure mechanism to verify the contents
#   of this file after exchange. Store public certificates in your home
#   directory, in the .curve subdirectory.

metadata
curve
    public-key = "7]g&M3GX##D.-!L>B.t?=@V6nkC34imk5/65kMNp"
```
### Example 2
--metadata email:foo@bar.org --metadata "street:tobaco road"
```sh
$ bx cert-public my_private_cert2 my_public_cert2 --metadata info@bar.org --metadata "street:tobaco road"
```
```sh
$ cat my_public_cert2
#   ****  Generated on 2015-02-16 02:01:57 by CZMQ  ****
#   ZeroMQ CURVE Public Certificate
#   Exchange securely, or use a secure mechanism to verify the contents
#   of this file after exchange. Store public certificates in your home
#   directory, in the .curve subdirectory.

metadata
    phone = "+1-603-555-1212"
    street = "tobaco road"
    email = "foo@bar.org"
curve
    public-key = "@)<n=8J0}=6j(-yjVcp*RfdVTT[0>Qkvq>hheMXK"
```
If a metadata element already exists in the private certificate the new value is ignored.