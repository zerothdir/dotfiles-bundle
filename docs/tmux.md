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

For jumping between projects, [sesh](sesh.md) is quicker than these:
`prefix` `K` opens its picker.

Closing the last window of a session switches you to another session instead
of exiting tmux.

## Windows

| Keys | What it does |
|---|---|
| `prefix` `c` | New window |
| `prefix` `0`…`9` | Go to window number |
| `prefix` `n` / `p` | Next / previous window |
| `prefix` `w` | Pick a window from a tree |
| `prefix` `,` | Rename the window |
| `prefix` `.` | Move the window to another number |
| `prefix` `&` | Close the window (asks first) |

Window names are the running command with an icon (for example the robot for
`claude`).

## Panes

| Keys | What it does |
|---|---|
| `prefix` `%` | Split side by side |
| `prefix` `"` | Split top and bottom |
| `prefix` arrow keys | Move to the pane in that direction |
| `prefix` `o` | Move to the next pane |
| `prefix` `;` | Move to the last used pane |
| `prefix` `Alt`+arrow keys | Resize by 5 cells (repeatable: keep pressing the arrow) |
| `prefix` `Ctrl`+arrow keys | Resize by 1 cell (repeatable) |
| `prefix` `z` | Zoom the pane to full window and back |
| `prefix` `Space` | Cycle through layouts |
| `prefix` `{` / `}` | Swap with the previous / next pane |
| `prefix` `!` | Move the pane into its own window |
| `prefix` `q` | Show pane numbers (press a number to jump) |
| `prefix` `x` | Close the pane (asks first) |

New windows and splits open in the directory the session started in.

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
| `prefix` `[` | Enter copy mode |
| `prefix` `PgUp` | Enter copy mode and scroll up a page |
| `h` `j` `k` `l`, `Ctrl+u` / `Ctrl+d` | Move, scroll half a page up / down |
| `/` / `?` | Search down / up (`n` / `N` for next / previous match) |
| `v` | Start selecting (`V` for whole lines) |
| `y` | Copy the selection and leave copy mode |
| `q` | Leave copy mode without copying |
| `prefix` `]` | Paste the last copied text |

Copy mode uses vi keys. `y` copies into tmux's own buffer, for pasting with
`prefix` `]`. To copy to your computer's clipboard instead, select with the
mouse as usual (tmux's mouse mode is off, so the terminal handles it). With
split panes that selects across all of them, so zoom the pane first with
`prefix` `z`.

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
