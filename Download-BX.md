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
410feedd4d614c0deb78b67b075f2b875d55a21f62a1f57c42e35738405e4aba

bx-osx-x64-mainnet v2.2.0
a5d36988da4ffce68879de49b063fe0f0c188349e21d99a4c2119c8f37d56534

bx-windows-x64-icu-mainnet.exe v2.2.0
66aec4a19dc6bd9669ab1c28be569952218925d790a6de7157ee90978ea71ed7
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1

iQEcBAEBAgAGBQJWd/OKAAoJEDzYwH8LXOFOna4H/2/yux7thgAX6WOr/fAtKI2s
FJVZMvb3k7o7cN+6xIyy5cWkK3KUJ72GAdqmPP1aYHaz8U3Tp3DlFJiJAa/IQBfB
QX+A2eJxReDoq92RdDntCoflIoEEivPn60YLBHlxaZe71qNCzJRvqFvGf1wiLxG6
UEfdJZWy1tM3EmF+USsz+FR4zi+OWj4bzHEOjf1EKNdj2Zl1TT3RtC3shW60l5eM
032oIVJ8CVDXiwh1mak5H2FPtZ8sX2zhSkIyDhu+Iz8nny0wHhUgh+z1GNYbwTlu
CiteAyzcjju8LFDPO5LekirowMPlSidf2pnqg2Ybz/kJXApYd0wpRxWeP4w8Ljk=
=A443
-----END PGP SIGNATURE-----
```

### Using BX to Calculate Hashes
With a previously-verified version of [BX](https://github.com/libbitcoin/libbitcoin-explorer/wiki) you can validate both the integrity of the download using the following commands.
```sh
$ bx base16-encode < bx-linux-x64-mainnet | bx sha256
410feedd4d614c0deb78b67b075f2b875d55a21f62a1f57c42e35738405e4aba

$ bx base16-encode < bx-osx-x64-mainnet | bx sha256
a5d36988da4ffce68879de49b063fe0f0c188349e21d99a4c2119c8f37d56534

$ bx base16-encode < bx-windows-x64-icu-mainnet.exe | bx sha256
66aec4a19dc6bd9669ab1c28be569952218925d790a6de7157ee90978ea71ed7
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