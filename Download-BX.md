# Version 3.0.0

### WARNING
These binaries are provided for your convenience. We cannot and do not guarantee that they will not lose your money or compromise your privacy. You are free to inspect the source code and build it yourself. **By downloading a binary copy of BX you accept all responsibility for its use and behavior.**

### Download
Each download is a single executable file.

| OS | File | Bytes |
|----|------|-------|
|![linux](https://github.com/libbitcoin/libbitcoin-explorer/wiki/linux.png) | [`bx-linux-x64-mainnet`](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v2.2.0/bx-linux-x64-mainnet) | `3,347,168` |
|![osx](https://github.com/libbitcoin/libbitcoin-explorer/wiki/osx.png) | [`bx-osx-x64-mainnet`](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v2.2.0/bx-osx-x64-mainnet) | `4,524,752` |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png) | [`bx-windows-x64-icu-mainnet.exe`](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v2.2.0/bx-windows-x64-icu-mainnet.exe) | `4,045,312` |

### Integrity Validation
Validate the integrity of the download by calculating a SHA-256 hash of the file and comparing the result to that in the signed message below. If you do not have a previously verified version of [BX](https://github.com/libbitcoin/libbitcoin-explorer/wiki) you can use any local or online [hash computer](http://onlinemd5.com) to calculate the hash values.

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

# Bitcoin Explorer v3.0.0

$ bx base16-encode < bx-linux-x64-qrcode | bx sha256
79c91d5714c1a2edf6c4610507e49d478c929d2e3fb5705fda1a1e31ce2c3f72

$ bx base16-encode < bx-osx-x64-qrcode | bx sha256
177c278c96d351cfc0655770a7e48674fc5ad77a7f4472af4542c1eb18e058ac

$ bx base16-encode < bx-windows-x64-icu.exe.exe | bx sha256
ad46a887bee8a0d4343cb2ff44a843f2d71ab33f3f860082e7d7f5fc20bb6633

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1

TODO
-----END PGP SIGNATURE-----

```

### Origin Validation
Validate the origin of the download by verifying the [PGP signature](http://en.wikipedia.org/wiki/Pretty_Good_Privacy) on the message containing the hashes (above). The message was signed by [evoskuil](https://twitter.com/evoskuil), which can be verified using the following public key. See also the [MIT Public Key Server](https://pgp.mit.edu/pks/lookup?op=get&search=0x3CD8C07F0B5CE14E).

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