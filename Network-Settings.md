The following network settings are implemented in [libbitcoin-network](https://github.com/libbitcoin/libbitcoin-network).
```ini
[network]
# The magic number for message headers, defaults to 3652501241 (use 118034699 for testnet).
identifier = 3652501241
# The number of times to retry contacting a node, defaults to 0.
connect_retries = 0
# The time limit for connection establishment, defaults to 5.
connect_timeout_seconds = 5
# The time limit to complete the connection handshake, defaults to 30.
channel_handshake_seconds = 30
# The peer hosts cache file path, defaults to 'hosts.cache'.
hosts_file = hosts.cache
# The debug log file path, defaults to 'debug.log'.
debug_file = debug.log
# The error log file path, defaults to 'error.log'.
error_file = error.log
# A seed node for initializing the host pool, multiple entries allowed, defaults shown.
seed = seed.bitcoin.sipa.be:8333
seed = dnsseed.bluematt.me:8333
seed = dnsseed.bitcoin.dashjr.org:8333
seed = seed.bitcoinstats.com:8333
seed = seed.bitcoin.jonasschnelli.ch:8333
seed = seed.voskuil.org:8333
# Testnet seed nodes.
#seed = testnet-seed.bitcoin.jonasschnelli.ch:18333
#seed = seed.tbtc.petertodd.org:18333
#seed = testnet-seed.bluematt.me:18333
#seed = testnet-seed.bitcoin.schildbach.de:18333
#seed = testnet-seed.voskuil.org:18333
```

Unless otherwise specified these settings apply to the [send-tx-node](bx-send-tx-node) and [send-tx-p2p](bx-send-tx-p2p) commands.

#### identifier
This is the network identifier passed in the header of each message on the peer-to-peer network.

#### connect_retries
The number of times to retry contacting a manually-configured peer before giving up. If this is set to zero it will retry forever. Used by the [send-tx-node](bx-send-tx-node) command only.

#### connect_timeout_seconds
The time in seconds to wait for initial connection to a peer.

#### channel_handshake_seconds
The time in seconds to wait to complete the version handshake with a peer.

#### hosts_file
The path to a file that contains the addresses of potential network peers. Used by the [send-tx-p2p](bx-send-tx-p2p) command only. If this has any addresses populated the seeding step will be skipped, greatly reducing command completion time.

#### debug_file

#### error_file

#### seed
