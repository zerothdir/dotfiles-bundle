# zoxide

A smarter `cd`. It remembers the directories you visit and jumps to the best
match for a few letters of the name. Here it sits behind `cd` itself, so you
don't need a separate command (`j` still works as an alias).

| Command | What it does |
|---|---|
| `cd foo` | Go to `./foo` if it exists; otherwise jump to the most used directory matching `foo` |
| `cd foo bar` | Match `foo`, then `bar`, in order (for example `cd proj api`) |
| `cd ~/some/path` | Works like a normal `cd` for real paths, and remembers them |
| `cd -` | Go back to the previous directory |
| `cd` | Go home |
| `zoxide query foo` | Print the match without jumping |
| `zoxide query -l` | List every remembered directory, best first |
| `zoxide remove ~/old/path` | Forget a directory |

zoxide only knows directories you've been to, so `cd` into a new one by its
real path once first.

Matching is on the last part of the path first: `cd dot` finds
`~/Repositories/dotfiles` before `~/dotnet/stuff`.

This only changes `cd` in interactive shells. Scripts still get the normal
`cd`. If you need the plain builtin by hand, run `builtin cd foo`.

The remembered directories are also offered by [sesh](sesh.md).
