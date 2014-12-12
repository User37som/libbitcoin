### WARNING
These binaries are provided for your convenience. We cannot and do not guarantee that they will not lose your money or compromise your privacy. You are free to inspect the source code and build it yourself. **By downloading a binary copy of BX you accept all responsibility for its use and behavior.**

### Download
Each download is a single executable file.

| OS | File | Bytes | SHA-256 | Signed |
|----|------|-------|---------|--------|
|![osx](https://github.com/libbitcoin/libbitcoin-explorer/wiki/osx.png)        | [`bx-osx-x64-mainnet-2.0.0`]()     | `5,357,188` | [`a5..60`](#) | [`Hy..A=`](#) |
|![osx](https://github.com/libbitcoin/libbitcoin-explorer/wiki/osx.png)        | [`bx-osx-x64-testnet-2.0.0`]()     | `5,357,188` | [`d6..29`](#) | [`IJ..I=`](#) |
|![linux](https://github.com/libbitcoin/libbitcoin-explorer/wiki/linux.png)    | [`bx-ubuntu-x64-mainnet-2.0.0`]()  | `3,664,376` | [`6a..f6`](#) | [`Hw..U=`](#) |
|![linux](https://github.com/libbitcoin/libbitcoin-explorer/wiki/linux.png)    | [`bx-ubuntu-x64-testnet-2.0.0`]()  | `3,664,376` | [`61..53`](#) | [`H6..I=`](#) |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png)| [`bx-windows-x64-mainnet-2.0.0`]() | `4,063,232` | [`f7..da`](#) | [`IG..Y=`](#) |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png)| [`bx-windows-x64-testnet-2.0.0`]() | `4,062,720` | [`bf..4b`](#) | [`II..I=`](#) |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png)| [`bx-windows-x86-mainnet-2.0.0`]() | `2,945,024` | [`cf..00`](#) | [`H0..4=`](#) |
|![windows](https://github.com/libbitcoin/libbitcoin-explorer/wiki/windows.png)| [`bx-windows-x86-testnet-2.0.0`]() | `2,944,512` | [`e1..80`](#) | [`Hw..g=`](#) |

### Origin Verification
With a previously-verified version of BX you can verify the integrity and origin of a subsequent version using the [`message-validate`](bx-message-validate) command as follows. The address for validation is `1GpL7EH3QFeG89mZf7dKKssYf4gjrH4mu7` (which should be independently verified).

```sh
$ bx message-validate 1GpL7EH3QFeG89mZf7dKKssYf4gjrH4mu7 HyTjsXlSGktaG2W9wbnhzdvRohZSs4kH5DP4lUqDmy2DXoLMo9P5kAVAdf54sPGmycHwVo0kevxM0pdkk6AU2XA= < bx-osx-x64-mainnet-2.0.0
```

### Initial Origin Verification

**File Validation**
First verify the integrity of the download by [performing a SHA-1 hash](http://onlinemd5.com) on the file and comparing the resulting value to the that in the table above. The encoding is base-16 and therefore not case sensitive.

**Signature Validation**
Next verify the signature of the 

### Testnet vs. Mainnet
BX depends on the [libbitcoin](https://github.com/libbitcoin/libbitcoin) toolkit, which currently requires recompilation for use with [testnet](https://en.bitcoin.it/wiki/Testnet). BX also provides [configuration settings](https://github.com/libbitcoin/libbitcoin-explorer/wiki/Configuration-Settings) for testnet. Each build can self-identify as testnet vs. mainnet using the [`settings`](bx-settings) command.
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