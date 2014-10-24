Get the block header from the specified hash or height. Height is ignored if both are specified.
```sh
$ bx fetch-header --help
```
```
Usage: bx fetch-header [-h] [--config VALUE] [--format VALUE] [--hash    
VALUE] [--height VALUE]                                                  

Info: Get the block header from the specified hash or height. Height is  
ignored if both are specified. Requires an Obelisk server connection.    

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.
-s [--hash]          The Base16 block hash.                              
-t [--height]        The block height.
```
This command supports [configuration settings](Configuration-Settings).
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
### Example 2
--height 1
```sh
$ bx fetch-header -t 1
```
```js
header
{
    bits 486604799
    hash 00000000839a8e6886ab5951d76f411475428afc90947ee320161bbf18eb6048
    merkle_tree_hash 0e3e2357e806b6cdb1f70b54c3a3a17b6714ee1f0e68bebb44a74b1efd512098
    nonce 2573394689
    previous_block_hash 000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f
    time_stamp 1231469665
    version 1
}
```

> Notice that the `header.previous_block_hash` property matches the `header.hash` property returned for the height 0 request.

### Example 3
--hash [[genesis block hash](https://en.bitcoin.it/wiki/Genesis_block)]
```sh
$ bx fetch-header -s 000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f
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
### Example 4
--height 1 --hash [[genesis block hash](https://en.bitcoin.it/wiki/Genesis_block)]
```sh
$ bx fetch-header -t 1 -s 000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f
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

> The genesis block is height 0. Notice that height is ignored when both hash and height are specified. To test a height against a hash request the hash based on height alone and then compare the hash value against the returned `header.hash` property.