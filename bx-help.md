Get the list of commands.
```sh
$ bx help --help
```
```
Usage: bx help [-h] [--config VALUE] [COMMAND]

Info: Get the list of commands.

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this
                     command.

Arguments (positional):

COMMAND              The command for which help is requested.
```
The `help` command lists all not obsoleted commands by name. Like all commands, `help` supports the `--help` option (see above), which explains its function.

As show in [Example 2](#example-2), the `help` command is optional on the BX command line.
### Example 1
```sh
$ bx help
```
```
Usage: bx COMMAND [--help]

Version: 3.1.0

Info: The bx commands are:

address-decode
address-embed
address-encode
base16-decode
base16-encode
base58-decode
base58-encode
base58check-decode
base58check-encode
base64-decode
base64-encode
bitcoin160
bitcoin256
btc-to-satoshi
cert-new
cert-public
ec-add
ec-add-secrets
ec-multiply
ec-multiply-secrets
ec-new
ec-to-address
ec-to-ek
ec-to-public
ec-to-wif
ek-address
ek-new
ek-public
ek-public-to-address
ek-public-to-ec
ek-to-address
ek-to-ec
fetch-balance
fetch-header
fetch-height
fetch-history
fetch-public-key
fetch-stealth
fetch-tx
fetch-tx-index
fetch-utxo
hd-new
hd-private
hd-public
hd-to-ec
hd-to-public
help
input-set
input-sign
input-validate
message-sign
message-validate
mnemonic-new
mnemonic-to-seed
qrcode
ripemd160
satoshi-to-btc
script-decode
script-encode
script-to-address
seed
send-tx
send-tx-node
send-tx-p2p
settings
sha160
sha256
sha512
stealth-decode
stealth-encode
stealth-public
stealth-secret
stealth-shared
token-new
tx-decode
tx-encode
tx-sign
uri-decode
uri-encode
validate-tx
watch-address
watch-stealth
watch-tx
wif-to-ec
wif-to-public
wrap-decode
wrap-encode

Bitcoin Explorer home page:

https://github.com/libbitcoin/libbitcoin-explorer
```
### Example 2
shortcut
```sh
$ bx
```
```
Usage: bx COMMAND [--help]

Version: 3.1.0

Info: The bx commands are:

address-decode
address-embed
address-encode
base16-decode
base16-encode
base58-decode
base58-encode
base58check-decode
base58check-encode
base64-decode
base64-encode
bitcoin160
bitcoin256
btc-to-satoshi
cert-new
cert-public
ec-add
ec-add-secrets
ec-multiply
ec-multiply-secrets
ec-new
ec-to-address
ec-to-ek
ec-to-public
ec-to-wif
ek-address
ek-new
ek-public
ek-public-to-address
ek-public-to-ec
ek-to-address
ek-to-ec
fetch-balance
fetch-header
fetch-height
fetch-history
fetch-public-key
fetch-stealth
fetch-tx
fetch-tx-index
fetch-utxo
hd-new
hd-private
hd-public
hd-to-ec
hd-to-public
help
input-set
input-sign
input-validate
message-sign
message-validate
mnemonic-new
mnemonic-to-seed
qrcode
ripemd160
satoshi-to-btc
script-decode
script-encode
script-to-address
seed
send-tx
send-tx-node
send-tx-p2p
settings
sha160
sha256
sha512
stealth-decode
stealth-encode
stealth-public
stealth-secret
stealth-shared
token-new
tx-decode
tx-encode
tx-sign
uri-decode
uri-encode
validate-tx
watch-address
watch-stealth
watch-tx
wif-to-ec
wif-to-public
wrap-decode
wrap-encode

Bitcoin Explorer home page:

https://github.com/libbitcoin/libbitcoin-explorer
```