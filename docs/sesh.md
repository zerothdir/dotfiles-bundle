# sesh

tmux session manager. Pick a directory or an existing session, and sesh
attaches to it, creating the session (named after the directory) if needed.
Works from inside or outside tmux.

## Picker

| Where | Keys | Lists |
|---|---|---|
| tmux | `prefix` `K` | Everything: tmux sessions, configured sessions and zoxide directories, with icons |
| zsh | `Alt+s` | Running tmux sessions and configured sessions |

Type to fuzzy filter (the filter is [gum](gum.md)), use the arrows to move,
`Enter` to connect and `Esc` to cancel.

## Commands

| Command | What it does |
|---|---|
| `sesh connect <dir or name>` | Attach to, or create, a session |
| `sesh list` | List everything sesh knows about |
| `sesh list -t` | Only running tmux sessions |
| `sesh list -z` | Only [zoxide](zoxide.md) directories |
| `sesh list -c` | Only sessions from the sesh config |
| `sesh list -i` | Add icons |
| `sesh last` | Switch to the previous session |

`sesh list` includes zoxide's directories, so any directory you've visited with
`j` can become a session.

## Config (optional)

Named sessions with a startup command go in `~/.config/sesh/sesh.toml`
(not managed by chezmoi):

```toml
[[session]]
name = "dotfiles"
path = "~/.local/share/chezmoi"
startup_command = "nvim"
```
