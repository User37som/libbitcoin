Commands are named with several objectives in mind. Congruence with the [SX command set](https://sx.dyne.org/quickstart.html) and brevity are important considerations, but in many cases these have taken a back seat to internal consistency and transparency.

#### Networking
Commands are generally named so that related commands sort together. In the case of network commands (`fetch-`, `send-`, `validate-` and `watch-`) the command's action (verb) starts the name. In other commands (e.g. `tx-`, `address-`) the primary data type (noun) starts the name. This distinction is primarily based on the congruence objective and also tends to read more naturally.

#### Conversion
Commands that convert from one data type to another are named using the "input-to-output" nomenclature. In certain cases the second data type is implied and the `-encode`/ `-decode` suffixes are used instead. This distinction is a nod to the congruence objective.

#### Hashing
Commands that hash data are named only with the type of hash. In these cases the data type of both the input and the output data type is Base16. As is the nature of hashing, these operations are not reversible and are therefore singletons.

#### Stealth
Commands pertaining to stealth addresses are prefixed with `stealth-` to differentiate them from bitcoin address commands.

#### Validation
Commands preixed or suffixed with `validate` have a third result code state: **invalid** (1). This is in addition to success / **valid** (0) and **failure** (-1), which may be returned by any command.

#### Other
Commands suffixed with `-new` create a new instance of whatever type is specified in the command. Other command actions (e.g. `-set`, `-sign`, `-add`, `-multiply`, `-uncover`) are unique to the contexts in which they are defined.

#### Command Map
The following diagrams show the full set of commands, input/output data types and relationships. Commands are grouped according to metadata categorization.

##### Wallet Commands
```
Commands pertaining to bitcoin keys and payment addresses.
```
<img src="/img/wallet-commands.png" width="30%" height="30%"></img>

##### Stealth Commands
```
Commands pertaining to stealth payments and addresses.
```
<img src="/img/stealth-commands.png" width="30%" height="30%"></img>

##### Transaction Commands
```
Commands pertaining to manipulation of transactions, excluding network calls.
```
<img src="/img/transaction-commands.png" width="30%" height="30%"></img>

##### Messaging Commands
```
Commands pertaining to signing and verifying arbitrary messages.
```
<img src="/img/messaging-commands.png" width="30%" height="30%"></img>

##### Online Commands
```
Commands that communicate on the bitcoin network.
```
<img src="/img/online-commands.png" width="30%" height="30%"></img>

##### Encoding Commands
```
Commands pertaining to encoding data to and from the various bitcoin formats.
```
<img src="/img/encoding-commands.png" width="30%" height="30%"></img>

##### Hash Commands
```
Commands pertaining to hashing data in the various bitcoin formats.
```
<img src="/img/hash-commands.png" width="30%" height="30%"></img>

##### Math Commands
```
Coin conversion and commands that perform secp256k1 elliptic curve math.
```
<img src="/img/math-commands.png" width="25%" height="25%"></img>