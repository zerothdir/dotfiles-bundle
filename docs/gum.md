# gum

Building blocks for interactive shell scripts. Here it draws the fuzzy filter
in the [sesh](sesh.md) picker, but it's handy in your own scripts too.

| Command | What it does |
|---|---|
| `ls \| gum filter` | Fuzzy pick one line from the input |
| `gum filter --no-limit` | Pick several (`Tab` to mark) |
| `gum choose a b c` | Pick from a short list with arrows |
| `gum input --placeholder "Name"` | Ask for one line of text |
| `gum write` | Ask for multi-line text (`Ctrl+D` to finish) |
| `gum confirm "Delete?" && rm file` | Yes / no question; exits non-zero on no |
| `gum spin --title "Building" -- make` | Spinner while a command runs |
| `gum style --border rounded "Hi"` | Print styled text |
| `gum format -- "# Title"` | Render Markdown |

Example: check out a git branch by picking it:

```sh
git switch "$(git branch --format='%(refname:short)' | gum filter)"
```
