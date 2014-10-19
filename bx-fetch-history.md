Get list of output points, values, and spends for a Bitcoin address.
```sh
$ bx fetch-history --help
```
```
Usage: bx fetch-history [-h] [--config VALUE] [--format VALUE]           
[BITCOIN_ADDRESS]                                                        

Info: Get list of output points, values, and spends for a Bitcoin        
address. Requires an Obelisk server connection.                          

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json', and  
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BITCOIN_ADDRESS      The Bitcoin address. If not specified the address is
                     read from STDIN.
```
### Example 1
[134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz](https://blockchain.info/address/134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz)
```sh
$ bx fetch-history 134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz
```
```js
transfers
{
    transfer
    {
        input
        {
            hash b7354b8b9cc9a856aedaa349cffa289ae9917771f4e06b2386636b3c073df1b5
            height 247742
            index 0
        }
        output
        {
            hash 97e06e49dfdd26c5a904670971ccf4c7fe7d9da53cb379bf9b442fc9427080b3
            height 247683
            index 1
        }
        value 100000
    }
}
```

> The `output.height` property indicates the block height at which the output is confirmed. A missing value indicates that the output is unconfirmed.

> The `input` property indicates that the output has been spent. The `input.height` property indicates the block height at which the spend is confirmed. A missing value indicates that the spend is unconfirmed.

### Example 2
[13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe](https://blockchain.info/address/13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe)
```sh
$ bx fetch-history 13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe
```
```js
transfers
{
    transfer
    {
        output
        {
            hash b7354b8b9cc9a856aedaa349cffa289ae9917771f4e06b2386636b3c073df1b5
            height 247742
            index 0
        }
        value 90000
    }
}
```

> A missing `input` property indicates that the output is unspent. The output for this example could become spent, and/or more output may be spent to this address.