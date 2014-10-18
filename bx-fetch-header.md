Get the block header from the specified hash or height. Height is ignored if both are specified.
```sh
$ bx fetch-header [-h] [--config VALUE] [--format VALUE] [--hash    
VALUE] [--height VALUE]                                                  
```
```
Info: Get the block header from the specified hash or height. Height is  
ignored if both are specified. Requires an Obelisk server connection.    

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'json', 'xml', 'info'
                     or 'native', defaults to native.                    
-h [--help]          Get a description and instructions for this command.
-s [--hash]          The Base16 block hash.                              
-t [--height]        The block height.
```
### Example 1
--height 0
```sh
$ bx fetch-header
```
```js
header
{
    bits 486604799
    hash 000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f
    merkle_tree_hash 4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b
    nonce 2083236893
    previous_block_hash 0000000000000000000000000000000000000000000000000000000000000000
    time_stamp 1231006505
    version 1
}
```
