# Offline Transactions
Generate a private key from a random seed value.
```sh
$ bx seed | bx ec-new
```
```
ce8f4b713ffdd2658900845251890f30371856be201cd1f5b3d970f793634333
```
Make a Bitcoin address from the private key.
```
$ bx ec-to-public ce8f4b713ffdd2658900845251890f30371856be201cd1f5b3d970f793634333 | bx ec-to-address
```

```
```
Now send some money (0.001 BTC) to the address `13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe`
```
```
```