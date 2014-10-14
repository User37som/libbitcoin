### WARNING

> These binaries are provided as a convenience. We cannot and do not guarantee that the binary will not steal your money or invade your privacy. If you desire such guarantees you are free to inspect the source code and build it yourself. **By downloading a binary copy of BX you accept all responsibility for its use and behavior.**

### Verification
You should verify that the binary you receive is the one that we published. The binary is a single file. Its authenticity can be determined by [performing a SHA256 hash](http://onlinemd5.com) on the file and comparing the resulting value to the following. The encoding is base-16 and therefore is case insensitive.
```
72e94972b341911328ce426bc8b34eb72c1a2756547fc96aaa9b08ef4591d469
```
Trusted versions of BX can also be used to verify other versions. The following command pipes `bx.exe` from the `new/` subdirectory into the `BASE16` argument of the [sha256 command](bx-sha256) to the same effect.
```sh
$ bx base16-encode < new/bx.exe | bx sha256
```