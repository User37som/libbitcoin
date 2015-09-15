There are two standard ways of encrypting a wallet seed. The [Key Encryption](#using-key-encryption) method allows you to encrypt an existing wallet seed. The [Mnemonic](#using-mnemonics) method requires you to accept a seed derived from an initial seed (which is not recoverable).

### Using Key Encryption
Create a new HD key.
```sh
$ bx seed -b 256 | bx hd-new
```
```
c82425d18a88ea6c5a92d06bc4ee26bfaf1b8782e7c0537544ae6dd40bb5083b
xprv9s21ZrQH143K4EdfsuwWHdxaGgcwGkTB1f71fbzJNfJma1Xga5XE3LqYxXKkwJJLevsp16iDRyk35MwvmKEEyyqLkHQVziTNs6VtPr1xGM8
```

Encrypt the seed (using a stronger passphrase).
```sh
$ bx ec-to-ek "my passphrase" c82425d18a88ea6c5a92d06bc4ee26bfaf1b8782e7c0537544ae6dd40bb5083b
```
```
6PYVupXn6GTGVxpdVgamwbnTzh8hNAswxDeAhUc5ufTCRu8KZgjoSQEqSN
```

Verify your ability to recover the HD key.

```sh
$ bx ek-to-ec "my passphrase" 6PYVj8maQYA95fREvtpgBMFtbi7U2T1B85zyjmEPqC7MknXowoV7yKzHXL | bx hd-new
```
```
xprv9s21ZrQH143K2uNeWu3crjqwic1ocvMMwRSypQyMDTk4yQedZv8zkBVUeq2gztk2HQCAvqNLhUfcHhbD1RGFQ1TTqDSWfTLW4qkxsPMdjNG
```
### Using Mnemonics
The passphrase is optional but if not used the mnemonic must be kept secret. See also [Remembering a Seed](How-to-Remember-a-Wallet-Seed).