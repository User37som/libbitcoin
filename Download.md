### WARNING

> These binaries are provided as a convenience. We cannot and do not guarantee that the binary will not steal your money or invade your privacy. If you desire such guarantees you are free to inspect the source code and build it yourself. **By downloading a binary copy of BX you accept all responsibility for its use and behavior.**

### Download

| Platform | Version | SHA-1 |
|----------|---------|---------|
| Linux | 2.0-beta1 | |
| Macintosh | 2.0-beta1 | This build is not yet available. |
| [Windows](https://github.com/libbitcoin/libbitcoin-explorer/releases/download/v2.0-beta0/bx-windows-x86.exe) | 2.0-beta1 | f1249c9974a0d00fca5905b2fd4c7533ffb9e14d |

### Verification
You should verify that the binary you receive is the one that we published. The binary is a single file. Its authenticity can be determined by [performing a SHA-1 hash](http://onlinemd5.com) on the file and comparing the resulting value to the that in the table above. The encoding is base-16 and therefore is case insensitive.

### Self Verification
Trusted versions of BX can also be used to verify other versions. The following command pipes `bx.exe` from the `new/` subdirectory into the `BASE16` argument of the [sha160 command](bx-sha160).

> In the interest of consistency BX refers to SHA-1 by its less common name of SHA-160, since the algorithm produces a 160 bit value. BX is not optimized for large hashing operations so this script can take a couple of minutes to complete.

```sh
$ bx base16-encode < new/bx.exe | bx sha160
```