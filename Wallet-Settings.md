The following wallet settings are implemented in [libbitcoin](https://github.com/libbitcoin/libbitcoin).
```ini
[wallet]
# The wallet import format (WIF) key version, defaults to 128 (use 239 for testnet).
wif_version = 128
# The hierarchical deterministic (HD) public key version, defaults to 76067358 (use 70617039 for testnet).
hd_public_version = 76067358
# The hierarchical deterministic (HD) private key version, defaults to 76066276 (use 70615956 for testnet).
hd_secret_version = 76066276
# The pay-to-public-key-hash address version, defaults to 0 (use 111 for testnet).
pay_to_public_key_hash_version = 0
# The pay-to-script-hash address version, defaults to 5 (use 196 for testnet).
pay_to_script_hash_version = 5
# The transaction version, defaults to 1.
transaction_version = 1
```

#### wif_version
Used when working with WIF encoded private keys. It sets the default value for the `--version` option of the [ec-to-wif](bx-ec-to-wif) command.

#### hd_public_version
Used when working with HD public keys. It sets the default value for the `--public_version` option of the [hd-public](bx-hd-public) and [hd-to-ec](bx-hd-to-ec) commands, and for the `--version` option of the [hd-to-public](bx-hd-to-public) command.

#### hd_secret_version
Used when working with HD private keys. It sets the default value for the `--secret_version` option of the [hd-public](bx-hd-public) and [hd-to-ec](bx-hd-to-ec) commands, and for the `--version` option of the [hd-new](bx-hd-new) command.

#### pay_to_public_key_hash_version
Used when working with payment addresses. It sets the default value for the `--version` option of the following commands:
* [address-embed](bx-address-embed)
* [address-encode](bx-address-encode)
* [base58check-encode](bx-base58check-encode)
* [ec-to-address](bx-ec-to-address)
* [ec-to-ek](bx-ec-to-ek)
* [ek-address](bx-ek-address)
* [ek-new](bx-ek-new)
* [ek-public](bx-ek-public)
* [stealth-encode](bx-stealth-encode)
* [wrap-encode](bx-wrap-encode)