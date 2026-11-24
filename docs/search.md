# ripgrep and fd

Fast search from the command line. Both skip files ignored by `.gitignore`
and hidden files by default. Neovim's search keys use them too.

## ripgrep (`rg`): search inside files

| Command | What it does |
|---|---|
| `rg foo` | Search for `foo` in the current directory, recursively |
| `rg -i foo` | Ignore case |
| `rg -w foo` | Whole words only |
| `rg -F 'a.b(c)'` | Literal text, not a regex |
| `rg foo src/` | Search only in `src/` |
| `rg -t py foo` | Only Python files (`rg --type-list` shows the types) |
| `rg -g '*.cu' foo` | Only files matching a glob |
| `rg -g '!test*' foo` | Exclude files matching a glob |
| `rg -l foo` | Only print file names |
| `rg -c foo` | Count matches per file |
| `rg -C 3 foo` | Show 3 lines of context around each match |
| `rg -uu foo` | Also search ignored and hidden files |
| `rg foo -r bar` | Preview replacing `foo` with `bar` (doesn't change files) |

## fd: find files by name

| Command | What it does |
|---|---|
| `fd foo` | Files and directories whose name contains `foo` |
| `fd -e cu` | Files with the `.cu` extension |
| `fd -t d foo` | Only directories (`-t f` for only files) |
| `fd foo src/` | Search only in `src/` |
| `fd -H foo` | Include hidden files |
| `fd -I foo` | Include ignored files |
| `fd -g '*.yaml'` | Glob instead of regex |
| `fd -e log -x rm` | Run a command on each result (here: delete `.log` files) |
| `fd -e cu -X wc -l` | Run one command with all results |

On Ubuntu the command may be `fdfind`; this setup links it as `fd`.
