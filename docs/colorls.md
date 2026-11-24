# colorls

`ls` with colors, file-type icons and git status. It's a separate command;
plain `ls` is unchanged.

| Command | What it does |
|---|---|
| `colorls` | List the current directory |
| `colorls -A` | Include hidden files (except `.` and `..`) |
| `colorls -l` | Long format (permissions, owner, size, date) |
| `colorls -lA --sd` | Long, hidden files, directories first |
| `colorls --gs` | Show git status for each file |
| `colorls --tree` | Tree view |
| `colorls --tree=2` | Tree view, 2 levels deep |
| `colorls -d` / `-f` | Only directories / only files |
| `colorls -t` | Sort by modification time |
| `colorls -S` | Sort by size |
| `colorls --report` | Summary counts of files and folders |
| `colorls --help` | Every option |

Tab completion for the options is loaded by `.zshrc`.

Icons need a Nerd Font in your terminal (FantasqueSansM Nerd Font here).

To use it as `ls`, add an alias to `~/.zshrc.local`:

```zsh
alias ls='colorls'
alias ll='colorls -lA --sd'
alias lt='colorls --tree=2'
```
