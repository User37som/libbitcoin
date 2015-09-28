It is possible to achieve the same objective using different combinations of commands.

#### Building a Payment Address

```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx bitcoin160 | bx address-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```
The same address results from the more general `base58check-encode` command in place of `address-encode`.
```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx bitcoin160 | bx base58check-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```
The same address results from the combination of the more general `wrap-encode` and `base58-encode` commands in place of `base58check-encode`.
```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx bitcoin160 | bx wrap-encode | bx base58-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
000423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b5728093a
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```
The same address results from the combination of the more general `sha256 ` and `ripemd160` commands in place of `bitcoin160`.
```sh
$ bx ec-new 9bb08de6bcc361df764c1edd9cc93059 | bx ec-to-public | bx sha256 | bx ripemd160 | bx wrap-encode | bx base58-encode
```
```
57b3a15beaf761a0dde5ee5da8634a80fa6508169feb26f62ca75573d7ae7ef6
031c9e4b5e45e636eac2b0bfff36530d6a048049dac66e88d3797371fadacb5040
bbd353249bf2360955621268b7db701454a20e7b5b2f42536c10a97712ad4895
0423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b
000423c50b6c4d2caa9fb3822eb0bc8e1f116ab43b5728093a
1NtZ6Dsj6vumHnAmA87aqLy6JhrsbpPKP
```