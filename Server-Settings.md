The following client-server settings are implemented in [libbitcoin-client](https://github.com/libbitcoin/libbitcoin-client).
```ini
[server]
# The URL of the default hidden testnet libbitcoin query service.
#url = tcp://rmrai2ifbed2bf55.onion:19091
# The URL of the default testnet libbitcoin query service.
#url = tcp://testnet.libbitcoin.net:19091
# The URL of the default hidden mainnet libbitcoin query service.
#url = tcp://sqax52n5enkw4dsj.onion:9091
# The URL of the default mainnet libbitcoin query service.
url = tcp://mainnet.libbitcoin.net:9091

# The address of a SOCKS5 proxy, defaults to none.
socks_proxy = 0.0.0.0:0
# The number of times to retry contacting a server, defaults to 0.
connect_retries = 0
# The time limit for connection establishment, defaults to 5.
connect_timeout_seconds = 5
# The Z85-encoded public key of the server, defaults to none.
#server_public_key =
# The Z85-encoded private key of the client, defaults to none.
#client_private_key =
```

#### url
The URL of the libbitcoin query service to use in all [online commands](Online-Commands) except for [send-tx-node](bx-send-tx-node) and [send-tx-p2p](bx-send-tx-p2p). See the list of [community servers](https://github.com/libbitcoin/libbitcoin-server/wiki/Community-Servers).

#### socks_proxy
The address of a SOCKS5 proxy to use when connecting to the specified URL. This can be used to connect though Tor.

#### connect_retries
The number of times to retry contacting the specified URL before giving up. If this is set to zero it will retry forever.

#### connect_timeout_seconds
The time in seconds to wait for a connection to the specified URL before giving up or retrying.

#### server_public_key
The public key of the server. If this is set the specified URL must be to the server's secure query endpoint (typically on port 9081). The client verifies the server identity and all communication with the server is encrypted.

#### client_private_key
The private key of the client. This can be generated using the [cert-new](bx-cert-new) command. The corresponding public key must be provided to the server for configuration, and can be generated from the private key using the [cert-public](bx-cert-public) command. When a server configures the public key of one or more clients, only those clients configured with corresponding private keys are allowed to connect. This configuration requires a `server_public_key` configuration as well.

