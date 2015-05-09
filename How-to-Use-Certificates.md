CurveZMQ is used for client/server authentication.

### Authenticating a server

Edit the [configuration file](Configuration-Settings) to include the server's public key:

``` ini
[mainnet]
# The URL of the Libbitcoin/Obelisk testnet server.
url =  tcp://obelisk-sol2.airbitz.co
# The Z85-encoded public key of the server certificate.
server_cert_key = CrWu}il)+MbqD60BV)v/xt&Xtwj*$[Q}Q{$9}hom
```

### Authenticating with a server

Some servers only allow authorised clients to communicate.

First, create a keypair:

``` sh
$ mkdir -p /path/to/cert
$ cd /path/to/cert
$ bx cert-new client.private
$ bx cert-public client.private client.public
```

Specify the private part in your config:

``` ini
[mainnet]
# The URL of the Libbitcoin/Obelisk testnet server.
url = tcp://strict-server-address:9091
# The path to the ZPL-encoded client private certificate file.
cert_file = /path/to/cert/client.private
```

Publish `client.public` and request the remote server operator to add it to their authorised client list.