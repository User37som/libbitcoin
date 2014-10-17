Perform a SHA160 (also known as SHA-1) hash of Base16 data.  
```sh
$ bx sha160 --help
```
```
Usage: bx sha160 [-h] [--config VALUE] [BASE16]                          

Info: Perform a SHA160 (also known as SHA-1) hash of Base16 data.        

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE16               The Base16 data to hash. If not specified the value 
                     is read from STDIN.
```
### Example 1
```sh
$ bx sha160 900df00d
```
```
ec5386a03e88b5ac9328f4eabe5103e601906daa
```
### Example 2
piped commands, [FIPS 180-2 SHA-1 Vector A](http://www.nsrl.nist.gov/testdata)
```sh
$ bx base16-encode abc | bx sha160
```
```
616263
ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f20015ad
```
### Example 3
piped commands, [FIPS 180-2 SHA-1 Vector B](http://www.nsrl.nist.gov/testdata)
```sh
$ bx base16-encode abcdbcdecdefdefgefghfghighijhijkijkljklmklmnlmnomnopnopq| bx sha160
```
```
6162636462636465636465666465666765666768666768696768696a68696a6b696a6b6c6a6b6c6d6b6c6d6e6c6d6e6f6d6e6f706e6f7071
248d6a61d20638b8e5c026930c3e6039a33ce45964ff2167f6ecedd419db06c1
```