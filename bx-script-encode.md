Base16 encode a plain text script.
```sh
$ bx script-encode --help
```
```
Usage: bx script-encode [-h] [--config VALUE] [SCRIPT]                   

Info: Base16 encode a plain text script.                                 

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SCRIPT               The plain text script tokens that make up the       
                     script. Multiple tokens must be quoted. If not      
                     specified the tokens are read from STDIN.
```
This command is helpful in interpreting scripts as they appear in the wire protocol, and for nesting scripts within scripts.

See also [script-decode](bx-script-decode).
### Example 1
[Bitcoin Wiki example](https://en.bitcoin.it/wiki/Script#Scripts)
```sh
$ bx script-encode "dup hash160 [ 89abcdefabbaabbaabbaabbaabbaabbaabbaabba ] equalverify checksig"
```
```
76a91489abcdefabbaabbaabbaabbaabbaabbaabbaabba88ac
```
### Example 2
piped commands
```sh
$ bx script-decode 76a91489abcdefabbaabbaabbaabbaabbaabbaabbaabba88ac | bx script-encode
```
```
dup hash160 [ 89abcdefabbaabbaabbaabbaabbaabbaabbaabba ] equalverify checksig
76a91489abcdefabbaabbaabbaabbaabbaabbaabbaabba88ac
```

### Example 3: Creating Multi-signature Addresses
Create a "2 of 4 multisig" payment address for a P2SH transaction to spend on the TEST ([196](https://github.com/libbitcoin/libbitcoin/wiki/BIP44-Altcoin-Version-Mappings#bip44-altcoin-version-mapping-table)) network. *The input script follows a pattern, and requires all 4 public addresses of the signatories that can authorize a P2SH transaction. Smaller compressed public keys are used in the example below.*  

```
echo "2 [ 020ae29f86f404e4b302cfa17ff15d93149af6a54c80a4172d47e41f55f6a78d73 ] [ 03664d528eb80096671ef9011c533ceb5df133238e3690d88f2960c786398b86b1 ] [ 029a449ea4a2155ea10002d704604bb3e8606631d35af20889a74b82b2dab572f6 ] [ 0321602d78046d63256b1730b119b1aca3428039f18fdb73ccf45ad3e148dd9b17 ] 4 checkmultisig" | bx script-encode | bx bitcoin160 | bx address-encode -v 196
```
```
2 [ 020ae29f86f404e4b302cfa17ff15d93149af6a54c80a4172d47e41f55f6a78d73 ] [ 03664d528eb80096671ef9011c533ceb5df133238e3690d88f2960c786398b86b1 ] [ 029a449ea4a2155ea10002d704604bb3e8606631d35af20889a74b82b2dab572f6 ] [ 0321602d78046d63256b1730b119b1aca3428039f18fdb73ccf45ad3e148dd9b17 ] 4 checkmultisig
ab572f6210321602d78046d63256b1730b119b1aca3428039f18fdb73ccf45ad3e148dd9b1754ae
abdc6bdb3646d67f6117047bbea7a419f1bf3578
2N8uwbECKZJLmfYRErQazYBAWfd8PJ66rAN
```

```2N8uwbECKZJLmfYRErQazYBAWfd8PJ66rAN``` is computed more directly by:

```
bx script-to-address "2 [ 020ae29f86f404e4b302cfa17ff15d93149af6a54c80a4172d47e41f55f6a78d73 ] [ 03664d528eb80096671ef9011c533ceb5df133238e3690d88f2960c786398b86b1 ] [ 029a449ea4a2155ea10002d704604bb3e8606631d35af20889a74b82b2dab572f6 ] [ 0321602d78046d63256b1730b119b1aca3428039f18fdb73ccf45ad3e148dd9b17 ] 4 checkmultisig"
```