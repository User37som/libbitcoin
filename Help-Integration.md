BX generates its help content from command metadata. The command name, description and parameterization are exposed by each command's generated class header. This allows BX to both locate a command by name and to enumerate all commands, and for each command emit the parameterization and/or description.

There is a command named `help` which lists the set of commands in alphabetical order to STDOUT. If BX is invoked without a command the `help` command is executed. These command lines are equivalent:
```sh
$ bx
$ bx help
```
Each command defines a `--help` option (which is implemented in shared code). Applied to any BX command, the help option causes BX to emit the command's help to STDOUT. Command help includes the command's description and full parameterization, including arguments and options with their descriptions and constraints. Similarly, the help command emits help for a specified command.

These command lines are equivalent:
```sh
$ bx address-decode --help
$ bx help address-decode
```
The help command also supports the `--help` option:
```sh
$ bx help --help
```
```
Get a description and instructions for this command.
```
An invalid command will result in a message to STDERR indicating that the command is not valid and to invoke `bx help` to see a list of commands.

Invalid parameterization on any command results in a message to STDERR indicating what parameterization is in error and that one may obtain help by using the command's `--help` option.