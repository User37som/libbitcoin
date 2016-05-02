There is a lengthy offering of [proof of Satoshi](http://www.drcraigwright.net/jean-paul-sartre-signing-significance/) on Dr. Wright's blog. The narrative is mostly tutorial, but also the following.

### Proof of the ability to base64 encode a phrase.
```
IFdyaWdodCwgaXQgaXMgbm90IHRoZSBzYW1lIGFzIGlmIEkgc2lnbiBDcmFpZyBXcmlnaHQsIFNh 
dG9zaGkuCgo=
```
```sh
$ bx base64-decode IFdyaWdodCwgaXQgaXMgbm90IHRoZSBzYW1lIGFzIGlmIEkgc2lnbiBDcmFpZyBXcmlnaHQsIFNhdG9zaGkuCgo=
```
```
Wright, it is not the same as if I sign Craig Wright, Satoshi.
```
### Proof of the ability to base64 encode old blockchain data.
```
------------------------- Signature File -------------------------
MEUCIQDBKn1Uly8m0UyzETObUSL4wYdBfd4ejvtoQfVcNCIK4AIgZmMsXNQWHvo6KDd2Tu6euEl1
3VTC3ihl6XUlhcU+fM4=
------------------------- End Signature --------------------------
```
```sh
$ bx base64-decode MEUCIQDBKn1Uly8m0UyzETObUSL4wYdBfd4ejvtoQfVcNCIK4AIgZmMsXNQWHvo6KDd2Tu6euEl13VTC3ihl6XUlhcU+fM4= | bx base16-encode
```
```
3045022100c12a7d54972f26d14cb311339b5122f8c187417dde1e8efb6841f55c34220ae0022066632c5cd4161efa3a2837764eee9eb84975dd54c2de2865e9752585c53e7cce
```
The data is extracted from the following transaction.
```sh
$ bx fetch-tx 828ef3b079f9c23829c56fe86e85b4a69d9e06e5b54ea597eef5fb3ffef509fe
```
Notice `transaction.inputs.input.script` matches decoding above (excluding the trailing `01` signature hash type byte).
```ini
transaction
{
    hash 828ef3b079f9c23829c56fe86e85b4a69d9e06e5b54ea597eef5fb3ffef509fe
    inputs
    {
        input
        {
            previous_output
            {
                hash 12b5633bad1f9c167d523ad1aa1947b2732a865bf5414eab2f9e5ae5d5c191ba
                index 1
            }
            script "[ 3045022100c12a7d54972f26d14cb311339b5122f8c187417dde1e8efb6841f55c34220ae0022066632c5cd4161efa3a2837764eee9eb84975dd54c2de2865e9752585c53e7cce01 ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 1ByLSV2gLRcuqUmfdYcpPQH8Npm8cccsFg
            script "[ 04bed827d37474beffb37efe533701ac1f7c600957a4487be8b371346f016826ee6f57ba30d88a472a0e4ecd2f07599a795f1f01de78d791b382e65ee1c58b4508 ] checksig"
            value 1000000000
        }
        output
        {
            address 12cbQLTFMXRnSzktFkuoG3eHoMeFtpTu3S
            script "[ 0411db93e1dcdb8a016b49840f8c53bc1eb68a382e97b1482ecad7b148a6909a5cb2e0eaddfb84ccf9744464f82e160bfa9b8b64f9d4c03f999b8643f656b412a3 ] checksig"
            value 1800000000
        }
    }
    version 1
}
```
### Proof of possession of a public key.
```
The command to export our public key is given below.
openssl ec -in sn-pub.pem -pubin -text -noout
        0411db93e1dcdb8a016b49840f8c53
        bc1eb68a382e97b1482ecad7b148a6
        909a5cb2e0eaddfb84ccf9744464f8
        2e160bfa9b8b64f9d4c03f999b8643
        f656b412a3
```
```sh
$ bx sha256 0411db93e1dcdb8a016b49840f8c53bc1eb68a382e97b1482ecad7b148a6909a5cb2e0eaddfb84ccf9744464f82e160bfa9b8b64f9d4c03f999b8643f656b412a3 | bx ripemd160
```
```
11b366edfc0a8b66feebae5c2e25a7b6a5d1cf31
```
```sh
$ bx address-encode 11b366edfc0a8b66feebae5c2e25a7b6a5d1cf31 --version 0
```
```
12cbQLTFMXRnSzktFkuoG3eHoMeFtpTu3S
```
The address of the public key has been used in 9 transactions to date.
```sh
$ bx fetch-history 12cbQLTFMXRnSzktFkuoG3eHoMeFtpTu3S
```
Notice `transfers.transfer[3].received.hash` is the same as `transaction.hash` above.
```ini
transfers
{
    transfer
    {
        received
        {
            hash 5d607ae88c2caf1329e758ccb1eb8a359f6df434ee84e03b9e14cea300a85f97
            height 409857
            index 0
        }
        value 66600
    }
    transfer
    {
        received
        {
            hash 20fb69a94413637cb50f65e473f91d2599a04d5a0bf9bf6a5e9e843df2710ea4
            height 228208
            index 0
        }
        value 30000
    }
    transfer
    {
        received
        {
            hash 1554a02d4eb1c7a73e3736922ed99530e360784e709896c42e5756e65b2da341
            height 220151
            index 2
        }
        value 1
    }
    transfer
    {
        received
        {
            hash 828ef3b079f9c23829c56fe86e85b4a69d9e06e5b54ea597eef5fb3ffef509fe
            height 248
            index 1
        }
        value 1800000000
    }
    transfer
    {
        received
        {
            hash 12b5633bad1f9c167d523ad1aa1947b2732a865bf5414eab2f9e5ae5d5c191ba
            height 183
            index 1
        }
        value 2800000000
    }
    transfer
    {
        received
        {
            hash 591e91f809d716912ca1d4a9295e70c3e78bab077683f79350f101da64588073
            height 182
            index 1
        }
        value 2900000000
    }
    transfer
    {
        received
        {
            hash a16f3ce4dd5deb92d98ef5cf8afeaf0775ebca408f708b2146c4fb42b41e14be
            height 181
            index 1
        }
        value 3000000000
    }
    transfer
    {
        received
        {
            hash f4184fc596403b9d638783cf57adfe4c75c605f6356fbc91338530e9831e9e16
            height 170
            index 1
        }
        value 4000000000
    }
    transfer
    {
        received
        {
            hash 0437cd7f8525ceed2324359c2d0ba26006d92d856a9c20fa0241106ee5a597c9
            height 9
            index 0
        }
        value 5000000000
    }
}
```
Retrieving the `transfers.transfer[8].received.hash` from above returns the following.
```sh
$ bx fetch-tx 0437cd7f8525ceed2324359c2d0ba26006d92d856a9c20fa0241106ee5a597c9
```
```ini
transaction
{
    hash 0437cd7f8525ceed2324359c2d0ba26006d92d856a9c20fa0241106ee5a597c9
    inputs
    {
        input
        {
            previous_output
            {
                hash 0000000000000000000000000000000000000000000000000000000000000000
                index 4294967295
            }
            script "[ 04ffff001d0134 ]"
            sequence 4294967295
        }
    }
    lock_time 0
    outputs
    {
        output
        {
            address 12cbQLTFMXRnSzktFkuoG3eHoMeFtpTu3S
            script "[ 0411db93e1dcdb8a016b49840f8c53bc1eb68a382e97b1482ecad7b148a6909a5cb2e0eaddfb84ccf9744464f82e160bfa9b8b64f9d4c03f999b8643f656b412a3 ] checksig"
            value 5000000000
        }
    }
    version 1
}
```
In other words the public key represents the address that received payment of the full award for block 9.

# No Proof

In newer standard transactions the public key of an address is not exposed on the blockchain until coin spent to the address is subsequently spent. Furthermore the public key of an address cannot be obtained from the address without reversing the `ripemd160` and `sha256` hashes, which is infeasible. However these are old transactions that use pay-to-public-key as opposed to pay-to-public-key-hash. The public key that Dr. Wright offered is actually exposed in `transaction.outputs.output.script` above.

So everything offered is public information.