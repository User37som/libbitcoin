Get metadata on potential payment transactions by stealth filter.
```sh
$ bx fetch-stealth --help
```
```
Usage: bx fetch-stealth [-h] [--config VALUE] [--format VALUE] [--height 
VALUE] [FILTER]                                                          

Info: Get metadata on potential payment transactions by stealth filter.  
Requires a Libbitcoin server connection.                                 

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json', and  
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.
-t [--height]        The minimum block height of transactions to include.

Arguments (positional):

FILTER               The Base2 stealth filter used to locate             
                     transactions. Defaults to all stealth transactions.
```
This command supports [configuration settings](Configuration-Settings).

In bx version 2.1 and later this command requires a [libbitcoin-server](https://github.com/libbitcoin/libbitcoin-server), in contrast to version 2.0 which requires an [obelisk server](https://github.com/spesmilo/obelisk).

The number of transactions matching a given prefix will increase over time. The minimum number of bits required by BS v3.0 is 8.
### Example 1
connecting to an Obelisk server (unsupported)
```sh
$ bx fetch-stealth 101010
```
```
timed out
```
### Example 2
```sh
$ bx fetch-stealth 101010
```
```
stealth
{
    match
    {
        ephemeral_public_key 03c35235b93427c39f477a83c493d2ea74d9195dc8a3b3e7dbb5ad88584b1472d2
        paid_address 1C8cs6vuuHqN7dtHqh13Yc6395unYcpSC6
        transaction_hash d216cd6596d4119acba1b8d786cdeb15f76f01d8a3ee12603e2581950857b736
    }
    match
    {
        ephemeral_public_key 037d2dc47d2cdef67eb84996b9df9d91d66624651d4902b82b1655f884f871328d
        paid_address 1EokigXmAJsZarQ7v36BYxeSy16gAAvZW4
        transaction_hash d3bff487e6b74141653035f6318545b129ca519ee0fecb616cdf764899ad23ff
    }
    match
    {
        ephemeral_public_key 0307d4526afaa699eec1d4b53570d08f56d12f825079ffeda9f6f41aa6fc943613
        paid_address 13LVHNKKc3kZrFF28foBY4pXwovMiZQ6gY
        transaction_hash 0406227a7d441e776d67d723da08a2d0e39714d0eb07d927cbf45dee8a2a23b9
    }
    match
    {
        ephemeral_public_key 03a386356c978169f1af8c69c8aa6ae5932c27919f5ebb6e9f05d728df6913f700
        paid_address 14ZrpgUDPuAsVXcei35MRFTv6oCYmPc1uV
        transaction_hash 2b0580d7aaf27a231a3905d45c332ba2c17bef343304d7486429b6e5b14c0294
    }
    match
    {
        ephemeral_public_key 03751bb00a3a57e070777fd543a9fa4709287b301c10dd15b1a6a0c48dc51815d2
        paid_address 12yqQstcLWJCPAUhUk8X3rpAZ6sYfDcvy3
        transaction_hash 87b98602c219fd0a492b43fe6954622ad304657e05dfb0bee92f338db8ba4bf4
    }
}
```
### Example 3
--format json, --height 325500, prefix 01
```sh
$ bx fetch-stealth -f json -t 325500 01
```
```js
{
    "stealth":
    [
        {
            "ephemeral_public_key": "022ec7cd1d0697e746c4044a4582db99ac85e9158ebd2c0fb2a797759ca418dd8d",
            "paid_address": "1GqSZbEXDQ98aDKhja33cAXRdT9Z8RhRuZ",
            "transaction_hash": "4e36b6ff5630631489ff40a18fe764051898ad032eb2e0a3af4c12c1e03475cc"
        },
        {
            "ephemeral_public_key": "03db09f00b2d6d939cdb7b8969d767671723183a926a3e6abd0ac3b1fa3e28bf75",
            "paid_address": "1Pjjg36UjWXJM3BrGLoDFLRLkb6F4E62t9",
            "transaction_hash": "73df6ec5211117fcee27bd1abe3039e23bca542df83abace0ad6bc9f7e274f57"
        },
        {
            "ephemeral_public_key": "0314e7655b91e34efb125de270879f0f14b9cfbddad7d35ba5bde07350ebe62e28",
            "paid_address": "1CWcNPRn4zbjrYfwrUTwFwyWqii8aiZqhg",
            "transaction_hash": "700c6d0a25533c47875d184d3dec3f46c695d8f9001cb3bf995d7ec7cb7b6ada"
        },
        {
            "ephemeral_public_key": "03e4805f75dfb336a20ba97d8b82d061f7234f41158f599b7c0f8e15ed44cf463d",
            "paid_address": "1BZYACk26cWwiqdCc2g51kjw6SnttKv1Z7",
            "transaction_hash": "b7fb2407b96b69e464c34519e5ef5f468959b03c0080cda0eba7a6c4ca1681c9"
        }
    ]
}
```

> Notice each transaction, for example [4e36b6ff...](https://blockchain.info/tx/4e36b6ff5630631489ff40a18fe764051898ad032eb2e0a3af4c12c1e03475cc), is identified with "Stealth Address Data". However this information may not be accurate due to changes in the stealth protocol.

### Example 4
redirect to file, all stealth transactions 
```sh
$ bx fetch-stealth -f xml > stealth.xml
```