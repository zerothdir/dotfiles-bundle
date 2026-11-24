# chezmoi

Dotfiles manager. It keeps the source copy of the dotfiles and writes them into
your home directory. Files it manages: `~/.zshrc`, `~/.tmux.conf`,
`~/.p10k.zsh`, `~/.gitconfig`, `~/.config/nvim`, `~/.config/clangd`,
`~/.config/tmux`.

Edit the source copy (or use `chezmoi edit`), not the file in your home:
`chezmoi apply` replaces home files with the source.

| Command | What it does |
|---|---|
| `chezmoi managed` | List managed files |
| `chezmoi diff` | Show what `apply` would change |
| `chezmoi apply` | Write the source to your home |
| `chezmoi edit ~/.zshrc` | Edit a file's source copy |
| `chezmoi edit --apply ~/.zshrc` | Edit, then apply when you save |
| `chezmoi re-add` | Copy changes you made directly in home back to the source |
| `chezmoi add ~/.file` | Start managing a file |
| `chezmoi forget ~/.file` | Stop managing a file (keeps it in home) |
| `chezmoi cd` | Open a shell in the source directory |
| `chezmoi source-path` | Print the source directory |
| `chezmoi doctor` | Check the setup |

Some files are templates (`.tmpl` in the source) that differ per OS. For
those, use `chezmoi edit`, since `re-add` can't update a template.

On a machine installed from the bundle, local changes to managed files are
replaced by the next bundle install. Keep machine-specific settings in
`~/.zshrc.local` and `~/.gitconfig.local` instead.
