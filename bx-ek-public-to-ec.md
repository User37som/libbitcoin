Extract the EC public key of an encrypted public key (BIP38).  
```sh
$ bx ek-public-to-ec --help
```
```
Usage: bx ek-public-to-ec [-h] [--config VALUE] PASSPHRASE               
[EK_PUBLIC_KEY]                                                          

Info: Extract the EC public key of an encrypted public key (BIP38).      

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

PASSPHRASE           The passphrase that was used to generate the        
                     encrypted private key.                              
EK_PUBLIC_KEY        The encrypted public key to decrypt. If not         
                     specified the key is read from STDIN.
```
**WARNING:** despite the term "confirmation code" the encrypted public key should never be used for confirmation. It is included as a command for completeness only. Instead confirm the encrypted private key using [ek-to-ec](bx-ek-to-ec) or [ek-to-address](bx-ek-to-address). For more information see [BIP38 Security Considerations](https://github.com/libbitcoin/libbitcoin/wiki/BIP38-Security-Considerations).

See also [ek-public-to-address](bx-ek-public-to-address).
### Example 1
lot/sequence
```sh
$ bx ek-public-to-ec "my passphrase" cfrm38VXASNzNjsak8pLc3ZtyPnBNDxAAbB18KMMCSjf8ZhW3FVTeuw2r9J3tyAUNyhfM7VMZuP
```
```
03d9cf7e2d52421ba735dc3aeca8a4b42e4fc272d4db6f7b311fb778bac7d4308d
```
### Example 2
```sh
$ bx ek-public-to-ec "my passphrase" cfrm38VUVm4ZGXku7wWGiLfAJNoeDHConFb9CugfTnR1SQC1jf3uwyKULmCMk4SUhsXasMyPcA9
```
```
037b49ab1aadf965a885932451c87de4265799cb29749f5713c2f8ace9d7e83875
```
### Example 3
piped commands
```sh
$ bx seed | bx ek-public passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq | bx ek-public-to-ec "my passphrase"
```
```
7113f4c2e8f67b61225c9a619cd984b63f28df434bf18217
cfrm38VURwDvZXxV2AfWnHe6GwDxSG4FkrK4en7VdaxLPMxMnU8BaLneNVAwf19TAkbmAptNNaH
0355ceb3cb0c6b1294c76cb9a6ebb61035c5e7220099647ce4c2df011ee7280460
```
### Example 4
incorrect passphrase
```sh
$ bx ek-public-to-ec "i forgot" cfrm38VURwDvZXxV2AfWnHe6GwDxSG4FkrK4en7VdaxLPMxMnU8BaLneNVAwf19TAkbmAptNNaH
```
```
The passphrase is incorrect.
```
### Example 5
--uncompressed
```sh
$ bx ek-public-to-ec "my passphrase" cfrm38V5FtqpFoBNE9wpKjp5Fe97tM7YX6brNPCjpb9uLiqENKfeHHUKLd2VrvQhuHVUwgNVaSt
```
```
047b49ab1aadf965a885932451c87de4265799cb29749f5713c2f8ace9d7e838753b15f90fb4032de40029a80c45bf9d8fc8653d81b4f18d36464840ddce50a4f9
```
### Example 6
--version 111 (testnet)
```sh
$ bx ek-public-to-ec "my passphrase" cfrm2zc7BCp4KwhEE6HzSSxVhUyj2ky8bzvSLEqmAPcakQXb49uFQ87UEg8EhbuwA33t8db2fYW
```
```
037b49ab1aadf965a885932451c87de4265799cb29749f5713c2f8ace9d7e83875
```
### Example 7
--version 48 (litecoin), --uncompressed
```sh
$ bx ek-public-to-ec "my passphrase" cfrm3B6UzSYXiZ36wznhsBGA2YdMrPq9VdxGetyK1VQ3o4A4bxiCY1h9XmUaK7M7tonUhBVyHBw
```
```
047b49ab1aadf965a885932451c87de4265799cb29749f5713c2f8ace9d7e838753b15f90fb4032de40029a80c45bf9d8fc8653d81b4f18d36464840ddce50a4f9
```