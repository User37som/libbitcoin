# Version 2.2.0

### WARNING
These binaries are provided for your convenience. We cannot and do not guarantee that they will not lose your money or compromise your privacy. You are free to inspect the source code and build it yourself. **By downloading a binary copy of BS you accept all responsibility for its use and behavior.**

### Download
Each download is a single executable file.

| OS | File | Bytes |
|----|------|-------|
|![linux](https://github.com/libbitcoin/libbitcoin-explorer/wiki/linux.png) | [`bx-linux-x64-mainnet`](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v2.2.0/bs-linux-x64-consensus-mainnet) | `3,347,168` |
|![osx](https://github.com/libbitcoin/libbitcoin-explorer/wiki/osx.png) | [`bx-osx-x64-mainnet`](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v2.2.0/bs-osx-x64-consensus-mainnet) | `4,524,752` |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png) | [`bx-windows-x64-icu-mainnet.exe`](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v2.2.0/bs-windows-x64-consensus-mainnet.exe) | `4,045,312` |

### Integrity Validation
Validate the integrity of the download by calculating a SHA-256 hash of the file and comparing the result to that in the signed message below. If you do not have a previously verified version of BX you can use any local or online [hash computer](http://onlinemd5.com) to calculate the hash values.

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

bx-linux-x64-mainnet v2.2.0
5a994749cde6c9cf5a07d052b60321b02bd55632a4681ed888150295b9e95ee4

bx-osx-x64-mainnet v2.2.0
5d0a0dba3adc1152dcfb65f65d4daca991f964603211b4c5f531bcf42ab4246a

bx-windows-x64-icu-mainnet.exe v2.2.0
7c2e627d3ee3e62937404c0f10bff052268a80d99cbdd24df486d0a2d974c929
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1

iQEcBAEBAgAGBQJWeBPeAAoJEDzYwH8LXOFOIYoH/i/NFg4ApcBjGbCLS1oD45bp
YaiEASdqsoqSDYIEmirZYcil2CtNlhc4vKYyNjkCsUpKP98JC0LP5L4jcxD/UQU4
PJIAn9Wu052chpg407DXnKMXNZ2e79pjrcAZAzMOIPfdQfwFlILpJ1DQUn/1AAXT
w7KI1lLD4iqZDAX0No2WikvPWjL7hE0/z5NR9cK3lHsdGvcl8ZfBwGA1PoHM/2mR
pnklHBVayKe/Qhfl4cMm3FNxDntAJ3r3FQ4hiogW831wU17gEDJ0vtBEt9PP9YYJ
QJTFawcZk8p/DqfoDPtHAiB+VLsJ+PdzCsj6R99fYbeYDYMkTQjxN/FH8/P4vUA=
=8nmG
-----END PGP SIGNATURE-----

```

### Using BX to Calculate Hashes
With a previously-verified version of [BX](https://github.com/libbitcoin/libbitcoin-explorer/wiki) you can validate both the integrity of the download using the following commands.
```sh
$ bx base16-encode < bx-linux-x64-mainnet | bx sha256
5a994749cde6c9cf5a07d052b60321b02bd55632a4681ed888150295b9e95ee4

$ bx base16-encode < bx-osx-x64-mainnet | bx sha256
5d0a0dba3adc1152dcfb65f65d4daca991f964603211b4c5f531bcf42ab4246a

$ bx base16-encode < bx-windows-x64-icu-mainnet.exe | bx sha256
7c2e627d3ee3e62937404c0f10bff052268a80d99cbdd24df486d0a2d974c929
```

### Origin Validation
Validate the origin of the download by verifying the [PGP signature](http://en.wikipedia.org/wiki/Pretty_Good_Privacy) on the message containing the hashes (above). The message was signed by [evoskuil](https://twitter.com/evoskuil), which can be verified using the following public key. See also the [MIT Public Key Server](https://pgp.mit.edu/pks/lookup?op=get&search=0x3CD8C07F0B5CE14E):

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.14 (GNU/Linux)

mQENBFLWPEoBCACfsNbsREA7RMRZmMD/a4eG2GYUlfjSjqI8d49tBhUTzM29hJ7F
gKbhNa62MFxUV3BA7Gg7t3JJj3zTXDzTg9FQVCZVlw1BlLPGTA6yYf5tQEY8h/z9
1wsoHDV9DQUl1ElpqaAYdMzdk6x1fuKQyP6kxKevtSO3BOkIrypJ7REeRlvOeHXb
WxeL+Ih07mvBCXG86SmEFYAGPmq5/0yIICc4cMNvh/Cf2BRI+9s40n2lCX9YIecF
rVxdtBZ3QWiOF2oRFBKplfuTPOUFker+owQgFFsFiRmgjLOtMOZkeGH8ctLT0zWn
CRVWvXwNkU3lueEp/uMPQdtVpBZFGL7DAgPvABEBAAG0H0VyaWMgVm9za3VpbCA8
ZXJpY0B2b3NrdWlsLm9yZz6JAT8EEwECACkFAlLWPEoCGw8FCQs2vfYHCwkIBwMC
AQYVCAIJCgsEFgIDAQIeAQIXgAAKCRA82MB/C1zhTjXqB/9K1EPQ/wt+Yd0bEjfd
YjO8Wb5cHAU14Lo7ElDV3JY/wGtZV9lELEJZyIIKTJ/FWJMt0fpPsnzkHh4XTbC9
cM6U0ujMVb2u+MbdaEpEvlsMomJtBzFehwLu+RcQlftPYKpPwMLT8NNJcBQbUJKP
/Ko5F5SlOGa/cEkWbKStiI6BDH9d2oOGMnULvSll4RryqQON2VVU5+gB+ebBUZPS
32HBPxGNrAbiBm5qPFEO6CHqFld7QHhRc3uO/33rzGZBxcuq7BdNr/3p6TfVK59d
tJ/XzF/74qCF2pEDedGGEr6dwYGMgeZNLapclCbfTnHJhYWzDuwMfR/1X4nwRCCM
0Ud0
=xE34
-----END PGP PUBLIC KEY BLOCK-----
```

### Testnet vs. Mainnet
BX depends on the [libbitcoin](https://github.com/libbitcoin/libbitcoin) toolkit, which currently requires recompilation for use with [testnet](https://en.bitcoin.it/wiki/Testnet). BX also provides [configuration settings](https://github.com/libbitcoin/libbitcoin-explorer/wiki/Configuration-Settings) for testnet. Each build can self-identify as testnet vs. mainnet using the [help](bx-help#example-1) command.
```sh
$ bx help
```
```
Usage: bx COMMAND [--help]

Version: 2.2.0 [mainnet]

Info: The bx commands are:

address-decode
address-embed
address-encode
...
```
