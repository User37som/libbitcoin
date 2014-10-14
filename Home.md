*The Bitcoin Command Line Tool*

This wiki contains a list of BX commands with examples (see menu on this page). The examples are drawn directly from BX [test cases](https://github.com/libbitcoin/libbitcoin-explorer/tree/master/test/commands) in the [source code](https://github.com/libbitcoin/libbitcoin-explorer). See the BX [readme](https://github.com/libbitcoin/libbitcoin-explorer/blob/master/README.md) for installation instructions and extensive developer documentation. If you encounter problems or have suggestions please use the BX [issues board](https://github.com/libbitcoin/libbitcoin-explorer/issues).

### License Overview

All files in this repository fall under the license specified in [COPYING](https://github.com/libbitcoin/libbitcoin-explorer/blob/master/COPYING). The project is licensed as [AGPL with a lesser clause](https://wiki.unsystem.net/en/index.php/Libbitcoin/License). It may be used within a proprietary project, but the core library and any changes to it must be published on-line. Source code for this library must always remain free for everybody to access.

### About Libbitcoin

The libbitcoin toolkit is a set of cross platform C++ libraries for building bitcoin applications. The toolkit consists of several libraries, most of which depend on the foundational [libbitcoin](https://github.com/libbitcoin/libbitcoin) library. Each library's repository can be cloned and built using common [automake](http://www.gnu.org/software/automake) instructions. There are no packages yet in distribution however each library includes an installation script (described below) which is regularly verified in the automated build.

### Background

Bitcoin Explorer is a fork of the popular [SX command line tool](https://sx.dyne.org/index.html). Many of the commands and their parameters are identical to SX although many have changed, some have been obsoleted and others have been added.

Obsoleted commands include those overtaken by industry standards or by changes to other commands. Others were based on interaction with network services other than the Bitcoin peer-to-peer network or [libbitcoin-server](https://github.com/libbitcoin/libbitcoin-server), making them redundant. Others were administrative interfaces to libbitcoin\_server and it was agreed that this scenario would be better handled independently.

Because of this significant interface change and out of a desire to provide consistent naming across repositories, the repository name of this fork is **libbitcoin-explorer**. Therefore the program is called **explorer** and is referred to as **BX** as a convenience and out of respect for its ground-breaking predecessor.