Extract the payment address of an encrypted public key (BIP38).  
```sh
$ bx ek-public-to-address --help
```
```
Usage: bx ek-public-to-address [-h] [--config VALUE] PASSPHRASE          
[EK_PUBLIC_KEY]                                                          

Info: Extract the payment address of an encrypted public key (BIP38).    

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

PASSPHRASE           The passphrase that was used to generate the        
                     intermediate passphrase token.                      
EK_PUBLIC_KEY        The encrypted public key from which to extract the  
                     payment address. If not specified the key is read   
                     from STDIN.    
```
**WARNING:** despite the term "confirmation code" the encrypted public key should never be used for confirmation. It is included as a command for completeness only. Instead confirm the encrypted private key using [ek-to-ec](bx-ek-to-ec) or [ek-to-address](bx-ek-to-address). For more information see [BIP38 Security Considerations](https://github.com/libbitcoin/libbitcoin/wiki/BIP38-Security-Considerations).

See also [ek-public-to-ec](bx-ek-public-to-ec).
### Example 1
lot/sequence
```sh
$ bx ek-public-to-address "my passphrase" cfrm38VXASNzNjsak8pLc3ZtyPnBNDxAAbB18KMMCSjf8ZhW3FVTeuw2r9J3tyAUNyhfM7VMZuP
```
```
1LoMVBxYZuzZZfTckU3JRccwFCMJYP3WRg
```
### Example 2
```sh
$ bx ek-public-to-address "my passphrase" cfrm38VUVm4ZGXku7wWGiLfAJNoeDHConFb9CugfTnR1SQC1jf3uwyKULmCMk4SUhsXasMyPcA9
```
```
1DeDt7odeJqJvquJ6obEZfH1hfJHMvnURa
```
### Example 3
piped commands
```sh
$ bx seed | bx ek-public passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq | bx ek-public-to-address "my passphrase"
```
```
7113f4c2e8f67b61225c9a619cd984b63f28df434bf18217
cfrm38VURwDvZXxV2AfWnHe6GwDxSG4FkrK4en7VdaxLPMxMnU8BaLneNVAwf19TAkbmAptNNaH
1DS3aqzg5w8bMsyzyutxcrhKoLZGjPnC13
```
### Example 4
incorrect passphrase
```sh
$ bx ek-public-to-address "i forgot" cfrm38VURwDvZXxV2AfWnHe6GwDxSG4FkrK4en7VdaxLPMxMnU8BaLneNVAwf19TAkbmAptNNaH
```
```
The passphrase is incorrect.
```
### Example 5
--uncompressed
```sh
$ bx ek-public-to-address "my passphrase" cfrm38V5FtqpFoBNE9wpKjp5Fe97tM7YX6brNPCjpb9uLiqENKfeHHUKLd2VrvQhuHVUwgNVaSt
```
```
1MydksvfdWNXM1KnVTS8A78M4b78aJcL1W
```
### Example 6
--version 111 (testnet)
```sh
$ bx ek-public-to-address "my passphrase" cfrm2zc7BCp4KwhEE6HzSSxVhUyj2ky8bzvSLEqmAPcakQXb49uFQ87UEg8EhbuwA33t8db2fYW
```
```
mtABBAtcTLGZhxNupNZcPaVLZetzHVWgAp
```
### Example 7
--version 111 (testnet), --uncompressed
```sh
$ bx ek-public-to-address "my passphrase" cfrm2zbi4iuQJ7cY69uJZsxhYLk4wLY7UWQiZ1wH5b3pEnzczSH3GHY3hAyV5AiWmU7mpk2Bqqc
```
```
n2Vb3w1eSXon87oQD2QVz2LfvahqVhBXKV
```