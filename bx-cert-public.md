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
$ 
```
```sh
```