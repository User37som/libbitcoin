Create a new mnemonic.
```sh
$ bx seed -b 128 | bx mnemonic-new
```
```
radar wreck account advance race sweet struggle advice basic spare deliver situate
```

Generate a new HD wallet from the seed (passphrase optional).
```sh
$ bx mnemonic-to-seed radar wreck account advance race sweet struggle advice basic spare deliver situate | bx hd-new
```
```
xprv9s21ZrQH143K2wbqNakRdoaatpMCevqHG5KKo1PBnk2jmuT1TDW272hcTdmsuBSQWv5PFnqh5CE6LrJac9gbZYcGpSG7sH3VynrWt3s9FDE
```

Verify your ability to recover the HD key.

```sh
$ bx mnemonic-to-seed radar wreck account advance race sweet struggle advice basic spare deliver situate | bx hd-new
```
```
xprv9s21ZrQH143K2wbqNakRdoaatpMCevqHG5KKo1PBnk2jmuT1TDW272hcTdmsuBSQWv5PFnqh5CE6LrJac9gbZYcGpSG7sH3VynrWt3s9FDE
```