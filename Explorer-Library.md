The BX build produces static and dynamic versions of a library. Tests are implemented in an executable called `libbitcoin_explorer_test` which links the library. The command line executable `bx` also links the library. This separation ensures that the library remains useful for building other applications.

In other words another application can link to `libbitcoin-explorer` and immediately take advantage of the full set of tested commands, as simple methods with no relation to the command line or STDIO.

Using the library requires inclusion of the header `<bitcoin/explorer.hpp>` and a reference to the `libbitcoin-explorer` library and its dependencies. To facilitate dependency management BX installs a standard [package config](http://en.wikipedia.org/wiki/Pkg-config).

Common functionality is exposed by the following namespaces:
```c++
bc::explorer::commands
bc::explorer::primitives
```