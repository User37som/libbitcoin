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

Save the encrypted private key `6PYVupXn6GTGVxpdVgamwbnTzh8hNAswxDeAhUc5ufTCRu8KZgjoSQEqSN` and memorize the passphrase `my passphrase`.

### Using Mnemonics
The passphrase is optional but if not used the mnemonic is not encrypted and therefore must be kept secret. See also [Remembering a Seed](How-to-Remember-a-Wallet-Seed).

Create a new mnemonic.
```sh
$ bx seed -b 128 | bx mnemonic-new
```
```
betray senior exhibit slot apart affair welcome dog hockey razor cart side
```

Generate a new HD wallet from the seed (using a stronger passphrase).
```sh
$ bx mnemonic-to-seed -p "my passphrase" betray senior exhibit slot apart affair welcome dog hockey razor cart side | bx hd-new
```
```
xprv9s21ZrQH143K38Jah6HduU5yGFkyDqtVDn24E1vjSMZ9vqdtCnUYn1v7pPedGoNvDFzjUG77VuYjWptQLsbCzqMy3AYXaWWFo7cbAvBxPqa
```

Verify your ability to recover the HD key.

```sh
$ bx mnemonic-to-seed -p "my passphrase" betray senior exhibit slot apart affair welcome dog hockey razor cart side | bx hd-new
```
```
xprv9s21ZrQH143K38Jah6HduU5yGFkyDqtVDn24E1vjSMZ9vqdtCnUYn1v7pPedGoNvDFzjUG77VuYjWptQLsbCzqMy3AYXaWWFo7cbAvBxPqa
```

Save the encrypted mnemonic (including word order) `betray senior exhibit slot apart affair welcome dog hockey razor cart side` and memorize the passphrase `my passphrase`.