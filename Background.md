Bitcoin Explorer is a major upgrade of the popular [SX](https://sx.dyne.org/index.html) command line tool. Many of the commands and their parameters are identical to SX although many have changed, some have been obsoleted and others have been added. Where command names differ BX redirects the user.

**Old command**

```sh
$ bx addr 03649860a9787e92db4b5371017e38ae36503f3007dc98498ef5f6cd7cfc4bfa4e
```
```
The 'addr' command has been replaced by 'ec-to-address'.
```
**New command**
```sh
$ bx ec-to-address 03649860a9787e92db4b5371017e38ae36503f3007dc98498ef5f6cd7cfc4bfa4e
```
```
18oMra2Aaj5iiWYkCeVQ1wbjXzYMqw46Kk
```
Obsoleted commands include those overtaken by industry standards or by changes to other commands. Others were based on interaction with network services other than the Bitcoin peer-to-peer network or [libbitcoin-server](https://github.com/libbitcoin/libbitcoin-server), making them redundant. Others were administrative interfaces to libbitcoin-server and it was decided that this scenario would be better handled independently.

Because of this significant interface change and out of a desire to provide consistent naming across repositories, the repository name of this fork is **libbitcoin-explorer**. Therefore the program is called **Bitcoin Explorer** and is referred to as **BX** as a convenience and out of respect for its ground-breaking predecessor.

This wiki contains a list of BX commands with examples (see menu on this page). The examples are drawn directly from BX [test cases](https://github.com/libbitcoin/libbitcoin-explorer/tree/version2/test/commands) in the [source code](https://github.com/libbitcoin/libbitcoin-explorer). The libbitcoin toolkit on which BX depends is a set of cross platform C++ libraries for building bitcoin applications. The toolkit consists of several libraries, most of which depend on the foundational [libbitcoin](https://github.com/libbitcoin/libbitcoin) library.