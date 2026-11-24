# tmux

Terminal multiplexer: sessions, windows and panes that keep running after you
disconnect.

The **prefix** is `Ctrl+Space`. "`prefix` `x`" means press `Ctrl+Space`,
let go, then press `x`.

## Sessions

| Command or keys | What it does |
|---|---|
| `tmux` | Start a new session |
| `tmux new -s name` | Start a session called `name` |
| `tmux ls` | List sessions |
| `tmux a` | Attach to the last session |
| `tmux a -t name` | Attach to session `name` |
| `prefix` `d` | Detach (the session keeps running) |
| `prefix` `s` | Pick a session from a tree |
| `prefix` `(` / `)` | Previous / next session |
| `prefix` `$` | Rename the session |
| `tmux kill-server` | Stop tmux and every session |

For jumping between projects, [sesh](sesh.md) is quicker than these.

Closing the last window of a session switches you to another session instead
of exiting tmux.

## Windows

| Keys | What it does |
|---|---|
| `prefix` `c` | New window, in the current directory |
| `prefix` `0`…`9` | Go to window number |
| `prefix` `n` / `p` | Next / previous window |
| `prefix` `w` | Pick a window from a tree |
| `prefix` `,` | Rename the window |
| `prefix` `<` / `>` | Move the window left / right (repeatable) |
| `prefix` `&` | Close the window (asks first) |

Window names are the running command with an icon (for example the robot for
`claude`).

## Panes

| Keys | What it does |
|---|---|
| `prefix` `\|` | Split side by side |
| `prefix` `-` | Split top and bottom |
| `prefix` `\` / `_` | Full-width / full-height split |
| `prefix` `h` `j` `k` `l` | Move to the pane left / down / up / right |
| `prefix` `H` `J` `K` `L` | Resize by 5 cells (repeatable: keep pressing the letter) |
| `prefix` `z` | Zoom the pane to full window and back |
| `prefix` `Space` | Cycle through layouts |
| `prefix` `{` / `}` | Swap with the previous / next pane |
| `prefix` `!` | Move the pane into its own window |
| `prefix` `q` | Show pane numbers (press a number to jump) |
| `prefix` `x` | Close the pane (asks first) |

New splits open in the current pane's directory.

## Floating scratch terminal

A popup terminal for quick commands. It's its own session, so it keeps its
state between openings.

| Keys | What it does |
|---|---|
| `prefix` `Alt+i` | Open / close the scratch terminal |
| `prefix` `Alt+h` | Turn the scratch terminal into a pane in the current window |
| `prefix` `Alt+l` | Turn the scratch terminal into a new window |
| `prefix` `Alt+m` | Turn the current pane into the scratch terminal (scratch must be unused) |

## Copy and scroll

| Keys | What it does |
|---|---|
| `prefix` `[` | Enter copy mode (scroll with arrows or `PgUp`/`PgDn`) |
| `prefix` `PgUp` | Enter copy mode and scroll up a page |
| `Ctrl+s` / `Ctrl+r` | In copy mode: search down / up |
| `q` | Leave copy mode |
| `prefix` `]` | Paste the last copied text |

Copy mode uses emacs keys, where `Ctrl+Space` starts a selection, but that's
also the prefix, so selecting inside copy mode doesn't work right now.

## Other

| Keys | What it does |
|---|---|
| `prefix` `?` | List every key binding |
| `prefix` `:` | tmux command prompt |
| `prefix` `R` | Reload `~/.tmux.conf` |
| `prefix` `I` | Install plugins (needs internet) |
| `prefix` `U` | Update plugins (needs internet) |

## Files

- `~/.tmux.conf`: the config (managed by chezmoi; see [chezmoi](chezmoi.md))
- `~/.tmux/plugins/`: plugins, installed by tpm
- `~/.config/tmux/tmux-nerd-font-window-name.yml`: extra window icons
