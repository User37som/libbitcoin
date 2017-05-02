# Version 3.2.0

### WARNING
These binaries are provided for your convenience. We cannot and do not guarantee that they will not lose your money or compromise your privacy. You are free to inspect the source code and build it yourself. **By downloading a binary copy of BX you accept all responsibility for its use and behavior.**

### Download
Each download is a single executable file.

| OS | File | Bytes |
|----|------|-------|
|![linux](https://github.com/libbitcoin/libbitcoin-explorer/wiki/linux.png) | [`bx-linux-x64-qrcode`](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v3.2.0/bx-linux-x64-qrcode) | `5,037,768` |
|![osx](https://github.com/libbitcoin/libbitcoin-explorer/wiki/osx.png) | [`bx-osx-x64-qrcode`](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v3.2.0/bx-osx-x64-qrcode) | `5,589,720` |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png) | [`bx-windows-x64-icu.exe`](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v3.2.0/bx-windows-x64-icu.exe) | `5,404,160` |

### Integrity Validation
Validate the integrity of the download by calculating a SHA-256 hash of the file and comparing the result to that in the signed message below. If you do not have a previously verified version of [BX](https://github.com/libbitcoin/libbitcoin-explorer/wiki) you can use any local or online [hash computer](http://onlinemd5.com) to calculate the hash values.

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

# Bitcoin Explorer v3.2.0

$ bx base16-encode < bx-linux-x64-qrcode | bx sha256
55f356f75c118df961e0442d0776f1d71e0b9e91936b1d9b96934f5eba167f0c

$ bx base16-encode < bx-osx-x64-qrcode | bx sha256
aa2311e4549cfddd47b9a7410889c075a2fa14812e9d9e6ddfe36631bf49f813

$ bx base16-encode < bx-windows-x64-icu.exe | bx sha256
862d3f5b5acf771fb2821d935abd00ab4bebcd86a1972ba4bd1a19dd5b8b3f7e

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v2.0.22 (GNU/Linux)

iQEcBAEBCAAGBQJZCM1QAAoJEDzYwH8LXOFO3OEH/jQxjqwHbuvVHwYS46FukKnP
IQkWF0H9Pzb8I1sutbnja+fJpBf/75SNLWb6ro3H/2IfkxEKCO8anWrk4+KTsWk8
0gs55LdqWvUtFVo6woYT+5mE1wD5cpJdodUuyEeRIXE7YwHE/YAFFQmJ4rMRSLsY
p4g0P6Ddt7R9TMpTDLMrymuIY20/fjbKohdfAsRywoq2JD8qasMM4/318xfv4dfi
aCouiI71PN7tIoujKKu9MbVjxK1e1F2YaKiEdVuwnVJe3ifwGj3MmNwfpIat1/cO
dJAn6Vuc9A7Cy3L34JwYOBOFaOYoNsIZZ8WgtJv1IPOwuWwCyRxc6pajlejCmRI=
=/ii4
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