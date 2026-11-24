# zsh

The shell, with zinit (plugin manager) and the powerlevel10k prompt.

## Keys

| Keys | What it does |
|---|---|
| `→` or `End` | Accept the grey autosuggestion (from your history) |
| `Alt+f` | Accept the next word of the suggestion |
| `Ctrl+R` | Search history for several words in any order; `Enter` runs, `Esc` cancels |
| `Alt+s` | [sesh](sesh.md) session picker |
| `Tab` | Complete; press again to cycle |
| `Ctrl+A` / `Ctrl+E` | Start / end of the line |
| `Ctrl+W` | Delete the previous word |
| `Ctrl+U` | Delete the whole line |
| `Ctrl+L` | Clear the screen |

Commands are syntax-highlighted as you type: red means zsh can't find the
command.

## Prompt (powerlevel10k)

| Command | What it does |
|---|---|
| `p10k configure` | Redo the prompt style wizard (writes `~/.p10k.zsh`) |

The prompt shows the directory, git branch and status, and the last command's
exit code and duration. Icons need a Nerd Font in your terminal.

## Plugins (zinit)

| Command | What it does |
|---|---|
| `zinit update` | Update all plugins (needs internet) |
| `zinit loaded` | List loaded plugins |
| `zinit times` | Show how long each plugin took to load |

## Files

| File | What it's for |
|---|---|
| `~/.zshrc` | The config. Managed by [chezmoi](chezmoi.md): edits get replaced on the next apply |
| `~/.zshrc.local` | Your own settings for this machine (env vars, aliases). Loaded last, never touched by updates |
| `~/.p10k.zsh` | Prompt style |

After changing a file, run `exec zsh` to reload.
