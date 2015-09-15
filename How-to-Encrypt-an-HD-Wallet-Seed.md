Create a new HD wallet using a 256 bit seed.
```sh
$ bx seed -b 256 | bx hd-new
```
```
dd8df8fbdefb4921383a3906d62bceb28f9630456318fd924aa1ee195ce8397e
xprv9s21ZrQH143K2uNeWu3crjqwic1ocvMMwRSypQyMDTk4yQedZv8zkBVUeq2gztk2HQCAvqNLhUfcHhbD1RGFQ1TTqDSWfTLW4qkxsPMdjNG
```

Encrypt the seed (using a stronger passphrase).
```sh
$ bx ec-to-ek "my passphrase" dd8df8fbdefb4921383a3906d62bceb28f9630456318fd924aa1ee195ce8397e
```
```
6PYVj8maQYA95fREvtpgBMFtbi7U2T1B85zyjmEPqC7MknXowoV7yKzHXL
```

Verify the seed encryption.

```sh
$ bx ek-to-ec "my passphrase" 6PYVj8maQYA95fREvtpgBMFtbi7U2T1B85zyjmEPqC7MknXowoV7yKzHXL
```
```
dd8df8fbdefb4921383a3906d62bceb28f9630456318fd924aa1ee195ce8397e
```

Discard the original seed and HD private key.