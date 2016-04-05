Create a QRCODE image file for a payment address.
```
$ bx help qrcode
```
```
Usage: bx qrcode [-hip] [--config value] [--density value] [--module_size
value] [--margin_size value] [--scheme value] [--version value]          
PAYMENT_ADDRESS                                                          

Info: Create a QRCODE image file for a payment address.                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-d [--density]       The pixels per inch of the QRCODE, defaults to 72.  
-h [--help]          Get a description and instructions for this command.
-i [--insensitive]   Do not use use sensitivity.                         
-m [--module_size]   The module size in pixels of the QRCODE, defaults to
                     8.                                                  
-p [--png]           Write the QRCODE in PNG file format.                
-r [--margin_size]   The margin size in pixels of the QRCODE, defaults to
                     2.                                                  
-s [--scheme]        The URI scheme of the QRCODE data, defaults to      
                     bitcoin.                                            
-v [--version]       The version of the QRCODE.                          

Arguments (positional):

PAYMENT_ADDRESS      The payment address. If not specified the address is
                     read from STDIN.         
```
### Example 1
--png
```
$ bx qrcode -p 131zKT2n1FN4Z6JdDAWMg3w8ehYjoRByTB > address.png
```
![qrcode](https://github.com/libbitcoin/libbitcoin-explorer/wiki/qrcode1.png)
### Example 2
--margin_size 5 --module_size 15 --png
```
$ bx qrcode -r 5 -m 15 -p 131zKT2n1FN4Z6JdDAWMg3w8ehYjoRByTB > address.png
```
![qrcode](https://github.com/libbitcoin/libbitcoin-explorer/wiki/qrcode2.png)
### Example 3
--margin_size 5 --module_size 15 --scheme litecoin --png
```
$ bx qrcode -r 5 -m 15 -s litecoin -p LhAq4Q2NQiCtP71ZWSZvURvniWsuKsyDjE > address.png
```
![qrcode](https://github.com/libbitcoin/libbitcoin-explorer/wiki/qrcode3.png)