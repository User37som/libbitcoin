# Offline Transactions
Generate a private key from a random seed value.
```sh
$ bx seed | bx ec-new
```
```
dbcd61584666028ac88798bacdc76f4b
4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350
```
Make a Bitcoin address from the private key.
```
$ bx ec-to-public 4ce3eb6bd06c224e3c355352a488720efc5ac9fe527a219ad35178c3cf762350 | bx ec-to-address
```
03e208f5403383c77d5832a268c9f71480f6e7bfbdfa44904becacfad66163ea31
1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6
```
```
Send some money (0.001 BTC) to the address `1JziqzXeBPyHPeAHrG4DCDW4ASXeGGF6p6`
```
```
```