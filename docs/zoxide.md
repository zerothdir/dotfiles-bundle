# zoxide

A smarter `cd`. It remembers the directories you visit and jumps to the best
match for a few letters of the name. Here the command is `j` (for jump).

| Command | What it does |
|---|---|
| `j foo` | Jump to the most used directory matching `foo` |
| `j foo bar` | Match `foo`, then `bar`, in order (for example `j proj api`) |
| `j ~/some/path` | Works like `cd` for real paths, and remembers them |
| `j -` | Go back to the previous directory |
| `j` | Go home |
| `ji foo` | Pick interactively among the matches |
| `j foo` then `Tab` | Complete from the matches |
| `zoxide query foo` | Print the match without jumping |
| `zoxide query -l` | List every remembered directory, best first |
| `zoxide remove ~/old/path` | Forget a directory |

zoxide only knows directories you've been to, so `cd` (or `j` with a full
path) into a new one once first.

Matching is on the last part of the path first: `j dot` finds
`~/Repositories/dotfiles` before `~/dotnet/stuff`.

The remembered directories are also offered by [sesh](sesh.md).
