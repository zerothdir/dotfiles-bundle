# dotfiles-bundle

An encrypted bundle of my dotfiles and tools for RHEL 9 (x86_64). It's built
from a private repo and is useless without the passphrase.

Download: <https://github.com/zerothdir/dotfiles-bundle/releases/download/rhel/rhel-bundle.tar.gz.gpg>

## Install

### 1. Download and copy (on Windows)

1. In the browser, download the bundle from the link above.
2. In PowerShell, copy it to the machine:

   ```powershell
   scp $HOME\Downloads\rhel-bundle.tar.gz.gpg <user>@<host>:
   ```

### 2. Install (on RHEL, over SSH)

1. Install the system packages. Do this once; you can skip it on later updates.
   colorls' dependencies need Ruby 3.2 or newer (RHEL 9's default is 3.0; the
   3.3 stream needs RHEL 9.4+):

   ```sh
   sudo dnf module enable -y ruby:3.3
   sudo dnf install -y zsh git tmux ruby ruby-devel gcc make util-linux-user
   ```

2. Decrypt and unpack the bundle. This asks for the passphrase:

   ```sh
   gpg --pinentry-mode loopback -d rhel-bundle.tar.gz.gpg | tar -xz
   ```

3. Run the installer, then clean up:

   ```sh
   cd rhel-bundle && ./install.sh
   cd .. && rm -rf rhel-bundle rhel-bundle.tar.gz.gpg
   ```

4. First time only:
   - Create `~/.zshrc.local` (environment variables for this machine) and
     `~/.gitconfig.local` (a `[user]` section with the git name and email for
     this machine). Updates never touch them.
   - Run `chsh -s "$(command -v zsh)"`. If that's refused (common on centrally
     managed accounts), add this to the end of `~/.bash_profile` instead:

     ```sh
     # Switch to zsh for interactive logins (chsh isn't allowed)
     if [ -t 1 ] && [ -x /usr/bin/zsh ]; then
       export SHELL=/usr/bin/zsh
       exec zsh -l
     fi
     ```

     `[ -t 1 ]` leaves `scp` and `ssh host command` alone, and `SHELL` makes
     tmux open zsh in new panes. If tmux was already running, restart it once
     with `tmux kill-server`.
   - Log out and back in.

If you already have a `~/.gitconfig` or `~/.zshrc`, the installer asks before
replacing it: move anything you want to keep into the local files first.

## Updating

Download the new bundle and repeat the steps above (skip the `dnf` step). The
local files aren't touched. The installer moves old directories aside as
`*.bak-<date>`; delete them once everything works.

Plugins, parsers and language servers come from the bundle, so update them by
installing a new bundle rather than with tmux's `Ctrl+Space` then `I`,
`:Lazy update` or Mason's install commands.

## Font on Windows

The prompt and tmux status bar use Nerd Font icons, which the Windows terminal
draws. Without admin rights you can still install a font for your user only:
download `FantasqueSansMono.zip` from the
[Nerd Fonts releases](https://github.com/ryanoasis/nerd-fonts/releases/latest),
right-click the `.ttf` files and choose **Install** (not *Install for all
users*), then pick **FantasqueSansM Nerd Font** in Windows Terminal →
Settings → your profile → Appearance → Font face.
