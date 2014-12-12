### WARNING
These binaries are provided for your convenience. We cannot and do not guarantee that they will not lose your money or compromise your privacy. You are free to inspect the source code and build it yourself. **By downloading a binary copy of BX you accept all responsibility for its use and behavior.**

### Download
Each download is a single executable file.

| OS | File | Bytes | SHA-1 | Signed |
|----|------|-------|-------|--------|
|![osx](https://github.com/libbitcoin/libbitcoin-explorer/wiki/osx.png)        | [`bx-osx-x64-mainnet-2.0.0`]()         | `5,357,188` | [`a5..60`](#a59227ab8b7b63a14f5faffcfd30ed30e47f0c60) | [`Hy..A=`](#HyTjsXlSGktaG2W9wbnhzdvRohZSs4kH5DP4lUqDmy2DXoLMo9P5kAVAdf54sPGmycHwVo0kevxM0pdkk6AU2XA=) |
|![osx](https://github.com/libbitcoin/libbitcoin-explorer/wiki/osx.png)        | [`bx-osx-x64-testnet-2.0.0`]()         | `5,357,188` | [`d6..29`](#d6e1dd461cbae487642bfd610a60024b8fd01029) | [`IJ..I=`](#IJ3kpajlbWmplyxkCAXOw4iQvN9GEENMOoncA1zp/j5+dcFOW72TmcLDixEWGqovAoUXqUuB81t4ujAeZnmc4tI=) |
|![linux](https://github.com/libbitcoin/libbitcoin-explorer/wiki/linux.png)    | [`bx-ubuntu-x64-mainnet-2.0.0`]()      | `3,664,376` | [`6a..f6`](#6ae4d2a9ce8f99a5f957bf37c6f341446bd6c1f6) | [`Hw..U=`](#Hw3UvUZChHdZNcP/NHriePf+xHUAzuApvOla6qS9LI5/I1PEGkdi/fz2NJGC5k29D0G2JPq07E8Tic1QM2Fe9IU=) |
|![linux](https://github.com/libbitcoin/libbitcoin-explorer/wiki/linux.png)    | [`bx-ubuntu-x64-testnet-2.0.0`]()      | `3,664,376` | [`61..53`](#61a621e74a439fa52da7ae7db80dbf73f95d6e53) | [`H6..I=`](#H6XpodRpfWGVVGPf+If6q7Mx1VfG42abgfMOnHnnM8fcKiDXPoncmP9C1IKOBsfpXEoQo6s+lahJggQRRWdtpaI=) |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png)| [`bx-windows-x64-mainnet-2.0.0`]() | `4,063,232` | [`f7..da`](#f7df1ca6519bf234651c0566cf5428a1b562b7da) | [`IG..Y=`](#IG2lZFMT3iQQzxibRj/Flxcuf2DgcgEKGyMi4gPhjg/sYhOvk9zDCZa95zBokA2jRW52v6/OeNHwRRJqk6xqxFY=) |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png)| [`bx-windows-x64-testnet-2.0.0`]() | `4,062,720` | [`bf..4b`](#bfaf406f20c5f0ffe641646342c8a12b2c203f4b) | [`II..I=`](#IIptIvhwmfnC+3t57kw9kKpuQwxEyKEAc2v5nbCgMWT6Ni618rjzk3c5KspSmFmCc8VLJ2RP7zQD/nw/zCdTu3I=) |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png)| [`bx-windows-x86-mainnet-2.0.0`]() | `2,945,024` | [`cf..00`](#cf43ca91dabd123048c8c1275a8f1e15443b0100) | [`H0..4=`](#H0BKoE4vkd65FPgatb5mOdO54i5VlnM8d4rbH+sjaku7KN8Rlc1Ie2zVzijt2TtcTGvYQUeK91LAHlMnS5YEAB4=) |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png)| [`bx-windows-x86-testnet-2.0.0`]() | `2,944,512` | [`e1..80`](#e1a7a9560b089b83cdd151726436b5857798d080) | [`Hw..g=`](#HwEKQUje+F5zZuWEOZ1ylsO5xWEg5bXwjUQb/hRdVQ1KW3QPvhgyplKq/C2Ra8uSd2o/py07u1GlybNhLVAY9fg=) |

### Origin Verification
With a previously-verified version of BX you can verify the integrity and origin of a subsequent version using the [message-validate](bx-message-validate) command as follows. The address for verification is `1GpL7EH3QFeG89mZf7dKKssYf4gjrH4mu7` (which should be independently verified).

```sh
$ bx message-validate 1GpL7EH3QFeG89mZf7dKKssYf4gjrH4mu7 HyTjsXlSGktaG2W9wbnhzdvRohZSs4kH5DP4lUqDmy2DXoLMo9P5kAVAdf54sPGmycHwVo0kevxM0pdkk6AU2XA= < bx-osx-x64-mainnet-2.0.0
```

### File Validation
You can verify the integrity of the download by [performing a SHA-1 hash](http://onlinemd5.com) on the file and comparing the resulting value to the that in the table above. The encoding is base-16 and therefore not case sensitive. This does not validate the origin of the file.

### Testnet vs. Mainnet
BX depends on the [libbitcoin](https://github.com/libbitcoin/libbitcoin) toolkit, which currently requires recompilation for use with [testnet](https://en.bitcoin.it/wiki/Testnet). BX also provides [configuration settings](https://github.com/libbitcoin/libbitcoin-explorer/wiki/Configuration-Settings) for testnet. Each build can self-identify as testnet vs. mainnet using the [settings](bx-settings) command.
```sh
$ bx settings
```
```js
settings
{
    general
    {
        network testnet
        retries 0
        wait 2000
    }
    mainnet
    {
        url tcp://obelisk.airbitz.co:9091
    }
    testnet
    {
        url tcp://obelisk-testnet.airbitz.co:9091
    }
}
```
See the value of the `settings.general.network` property above.