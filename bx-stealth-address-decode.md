Decode a stealth address.
```sh
$ bx stealth-address-decode --help
```
```
Usage: bx stealth-address-decode [-h] [--config VALUE] [--format VALUE]  
STEALTH_ADDRESS                                                          

Info: Decode a stealth address.                                          

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

STEALTH_ADDRESS      The stealth payment address.
```
### Example 1
scan key only
```sh
$ bx stealth-address-decode hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
```
stealth_address
{
    encoded hfFGUXFPKkQ5M6LC6aEUKMsURdhw93bUdYdacEtBA8XttLv7evZkira2i
    prefix ""
    scan_public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    signatures 1
    spend
    {
        public_key 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    }
    testnet false
}
```
```