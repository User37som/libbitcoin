### WARNING

These binaries are provided for your convenience. We cannot and do not guarantee that they will not lose your money or compromise your privacy. You are free to inspect the source code and build it yourself. **By downloading a binary copy of BX you accept all responsibility for its use and behavior.**

### Download
Each download is a single executable file.

| Platform | Bytes | SHA-1 | Signature |
|----------|-------|-------|-----------|
| [bx-osx-x64-mainnet-2.0.0]()         | 5,357,188 | [a5..60](#a59227ab8b7b63a14f5faffcfd30ed30e47f0c60) | [HyTj..2XA=](#HyTjsXlSGktaG2W9wbnhzdvRohZSs4kH5DP4lUqDmy2DXoLMo9P5kAVAdf54sPGmycHwVo0kevxM0pdkk6AU2XA=) |
| [bx-osx-x64-testnet-2.0.0]()         | 5,357,188 | [d6..29](#d6e1dd461cbae487642bfd610a60024b8fd01029) | [IJ3k..tI=](#IJ3kpajlbWmplyxkCAXOw4iQvN9GEENMOoncA1zp/j5+dcFOW72TmcLDixEWGqovAoUXqUuB81t4ujAeZnmc4tI=) |
| [bx-ubuntu-x64-mainnet-2.0.0]()      | 3,664,376 | [6a..f6](#6ae4d2a9ce8f99a5f957bf37c6f341446bd6c1f6) | [Hw3U..9IU=](#Hw3UvUZChHdZNcP/NHriePf+xHUAzuApvOla6qS9LI5/I1PEGkdi/fz2NJGC5k29D0G2JPq07E8Tic1QM2Fe9IU=) |
| [bx-ubuntu-x64-testnet-2.0.0]()      | 3,664,376 | [61..53](#61a621e74a439fa52da7ae7db80dbf73f95d6e53) | [H6Xp..paI=](#H6XpodRpfWGVVGPf+If6q7Mx1VfG42abgfMOnHnnM8fcKiDXPoncmP9C1IKOBsfpXEoQo6s+lahJggQRRWdtpaI=) |
| [bx-windows-x64-mainnet-2.0.0.exe]() | 4,063,232 | [f7..da](#f7df1ca6519bf234651c0566cf5428a1b562b7da) | [IG2l..xFY=](#IG2lZFMT3iQQzxibRj/Flxcuf2DgcgEKGyMi4gPhjg/sYhOvk9zDCZa95zBokA2jRW52v6/OeNHwRRJqk6xqxFY=) |
| [bx-windows-x64-testnet-2.0.0.exe]() | 4,062,720 | [bf..4b](#bfaf406f20c5f0ffe641646342c8a12b2c203f4b) | [IIpt..u3I=](#IIptIvhwmfnC+3t57kw9kKpuQwxEyKEAc2v5nbCgMWT6Ni618rjzk3c5KspSmFmCc8VLJ2RP7zQD/nw/zCdTu3I=) |
| [bx-windows-x86-mainnet-2.0.0.exe]() | 2,945,024 | [cf..00](#cf43ca91dabd123048c8c1275a8f1e15443b0100) | [H0BK..AB4=](#H0BKoE4vkd65FPgatb5mOdO54i5VlnM8d4rbH+sjaku7KN8Rlc1Ie2zVzijt2TtcTGvYQUeK91LAHlMnS5YEAB4=) |
| [bx-windows-x86-testnet-2.0.0.exe]() | 2,944,512 | [e1..80](#e1a7a9560b089b83cdd151726436b5857798d080) | [HwEK..9fg=](#HwEKQUje+F5zZuWEOZ1ylsO5xWEg5bXwjUQb/hRdVQ1KW3QPvhgyplKq/C2Ra8uSd2o/py07u1GlybNhLVAY9fg=) |

### Verification
You should verify that the binary you receive is the one that we published. Its authenticity can be determined by [performing a SHA-1 hash](http://onlinemd5.com) on the file and comparing the resulting value to the that in the table above. The encoding is base-16 and therefore is case insensitive.

### Self Verification
Trusted versions of BX can also be used to verify other versions. The following command pipes `bx.exe` from the `new/` subdirectory into the `BASE16` argument of the [sha160 command](bx-sha160). BX refers to SHA-1 by its less common name of SHA-160, since the algorithm produces a 160 bit value.
```sh
$ bx base16-encode < new/bx.exe | bx sha160
```

### Testnet vs. Mainnet
BX depends on the [libbitcoin](https://github.com/libbitcoin/libbitcoin) toolkit, which currently requires recompilation for use with [testnet](https://en.bitcoin.it/wiki/Testnet). BX also provides [configuration settings](https://github.com/libbitcoin/libbitcoin-explorer/wiki/Configuration-Settings) for testnet. Although because of the build requirement the effectiveness of these settings is limited.