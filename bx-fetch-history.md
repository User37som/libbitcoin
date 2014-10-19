
```sh
$ bx fetch-history --help
```
```

```
### Example 1
[134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz](https://blockchain.info/address/134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz)
```sh
$ bx fetch-history 134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz
```
```js

```

> The `output.height` property indicates the block height at which the output is confirmed. A missing value indicates that the output is unconfirmed.

> The `input` property indicates that the output has been spent. The `input.height` property indicates the block height at which the spend is confirmed. A missing value indicates that the spend is unconfirmed.

### Example 2
[13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe](https://blockchain.info/address/13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe)
```sh
$ bx fetch-history 13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe
```
```js

```

> A missing `input` property indicates that the output is unspent. The output for this example could become spent, and/or more output may be spent to this address.