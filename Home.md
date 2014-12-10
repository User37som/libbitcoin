*The Bitcoin Command Line Tool*

### About Bitcoin Explorer

BX is a major upgrade of the popular [SX command line tool](https://sx.dyne.org/index.html). Many of the commands and their parameters are identical to SX although many have changed, some have been obsoleted and others have been added.

#### Example
```sh
$ bx seed | bx ec-new | bx ec-to-public | bx ec-to-address
13ua8RRSxLpL5WL5cKUDepUCvJZgGWuKh7
```
Obsoleted commands include those overtaken by industry standards or by changes to other commands. Others were based on interaction with network services other than the Bitcoin peer-to-peer network or [libbitcoin-server](https://github.com/libbitcoin/libbitcoin-server), making them redundant. Others were administrative interfaces to libbitcoin-server and it was decided that this scenario would be better handled independently.

Because of this significant interface change and out of a desire to provide consistent naming across repositories, the repository name of this fork is **libbitcoin-explorer**. Therefore the program is called **Bitcoin Explorer** and is referred to as **BX** as a convenience and out of respect for its ground-breaking predecessor.

The libbitcoin toolkit is a set of cross platform C++ libraries for building bitcoin applications. The toolkit consists of several libraries, most of which depend on the foundational [libbitcoin](https://github.com/libbitcoin/libbitcoin) library.

This wiki contains a list of Bitcoin Explorer (BX) commands with examples (see menu on this page). The examples are drawn directly from BX [test cases](https://github.com/libbitcoin/libbitcoin-explorer/tree/version2/test/commands) in the [source code](https://github.com/libbitcoin/libbitcoin-explorer). See the BX [readme](https://github.com/libbitcoin/libbitcoin-explorer/blob/version2/README.md) for installation instructions and extensive developer documentation. If you encounter problems or have suggestions please use the BX [issues board](https://github.com/libbitcoin/libbitcoin-explorer/issues).
