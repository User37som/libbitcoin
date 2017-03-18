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