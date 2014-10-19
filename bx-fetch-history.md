Get list of output points, values, and spends for one or more Bitcoin addresses.
```sh
$ bx fetch-history --help
```
```
Usage: bx fetch-history [-h] [--config VALUE] [--format VALUE]           
[BITCOIN_ADDRESS]...                                                     

Info: Get list of output points, values, and spends for one or more      
Bitcoin addresses. Requires an Obelisk server connection.                

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'json', 'xml', 'info'
                     or 'native', defaults to native.                    
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BITCOIN_ADDRESS      The set of Bitcoin addresses. If not specified the  
                     addresses are read from STDIN.
```

> The `output.height` property indicates the block height at which the output is confirmed. A missing value indicates that the output is unconfirmed.

> The `input` property indicates that the output has been spent. The `input.height` property indicates the block height at which the spend is confirmed. A missing value indicates that the spend is unconfirmed.

### Example 1
[134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz](https://blockchain.info/address/134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz)
```sh
$ bx fetch-history 134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz
```
```js
history
{
    address 134HfD2fdeBTohfx8YANxEpsYXsv5UoWyz
    records
    {
        record
        {
            value 100000
            output
            {
                height 247683
                point
                {
                    hash 97e06e49dfdd26c5a904670971ccf4c7fe7d9da53cb379bf9b442fc9427080b3
                    index 1
                }
            }
            input
            {
                height 247742
                point
                {
                    hash b7354b8b9cc9a856aedaa349cffa289ae9917771f4e06b2386636b3c073df1b5
                    index 0
                }
            }
        }
    }
}
```
### Example 2
[13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe](https://blockchain.info/address/13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe)
```sh
$ bx fetch-history 13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe
```
```js
history
{
    address 13Ft7SkreJY9D823NPm4t6D1cBqLYTJtAe
    records
    {
        record
        {
            value 90000
            output
            {
                height 247742
                point
                {
                    hash b7354b8b9cc9a856aedaa349cffa289ae9917771f4e06b2386636b3c073df1b5
                    index 0
                }
            }
        }
    }
}
```