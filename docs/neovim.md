# Neovim

Editor, configured from kickstart.nvim. The **leader** key is `Space`.
Press `Space` and wait: a popup (which-key) lists what comes next.

## Finding things (Telescope)

| Keys | What it does |
|---|---|
| `Space` `s` `f` | Find files |
| `Space` `s` `g` | Search text in all files (live grep) |
| `Space` `s` `w` | Search for the word under the cursor |
| `Space` `Space` | Switch between open buffers |
| `Space` `s` `.` | Recent files |
| `Space` `/` | Fuzzy search in the current file |
| `Space` `s` `/` | Search text in open files |
| `Space` `s` `d` | Diagnostics (errors and warnings) |
| `Space` `s` `r` | Reopen the last search |
| `Space` `s` `h` | Search help |
| `Space` `s` `k` | Search keymaps (find any binding) |
| `Space` `s` `n` | Search the Neovim config files |

Inside a picker: type to filter, `Ctrl+n`/`Ctrl+p` or arrows to move, `Enter`
to open, `Ctrl+v`/`Ctrl+x` to open in a vertical/horizontal split, `Esc` to
close.

## Code (language servers)

| Keys | What it does |
|---|---|
| `g` `d` | Go to definition (`Ctrl+t` to come back) |
| `g` `r` | List references |
| `g` `I` | Go to implementation |
| `g` `D` | Go to declaration |
| `Space` `D` | Go to type definition |
| `K` | Show docs for the symbol under the cursor |
| `Space` `r` `n` | Rename the symbol everywhere |
| `Space` `c` `a` | Code actions (quick fixes) |
| `Space` `d` `s` | Symbols in this file |
| `Space` `w` `s` | Symbols in the project |
| `Space` `f` | Format the file |
| `Space` `t` `h` | Toggle inlay hints |
| `Space` `q` | Put all diagnostics in a list |
| `]` `d` / `[` `d` | Next / previous diagnostic |

Language servers: `clangd` (C, C++, CUDA), `lua_ls` (Lua), `gopls` (Go; the
bundle includes Go 1.26.1), `pyright` (Python, only if Node.js is installed).
`:LspInfo` shows what's attached to the current file.

Syntax highlighting (treesitter) covers Bash, C, C++, CUDA, CMake, Make, Go,
Python, Lua, JavaScript, HTML, XML, JSON, YAML, TOML, INI, SQL, Dockerfile,
Markdown, Vim script and git files. Other file types open with plain
highlighting.

For C++ and CUDA projects, clangd needs a `compile_commands.json` in the project
root (CMake: `-DCMAKE_EXPORT_COMPILE_COMMANDS=ON`).

## Completion

Completion (nvim-cmp) starts in insert mode. As you type, a menu pops up with
suggestions, and the first one is already highlighted. Nothing is inserted
until you accept.

| Keys | What it does |
|---|---|
| `Ctrl+y` | Accept the highlighted suggestion ("yes") |
| `Ctrl+n` / `Ctrl+p`, or `↓` / `↑` | Highlight the next / previous suggestion |
| `Ctrl+e` | Close the menu without accepting |
| `Ctrl+Space` | Open the menu when it isn't showing |
| `Ctrl+b` / `Ctrl+f` | Scroll the documentation popup beside the menu |
| `Ctrl+l` / `Ctrl+h` | After accepting a snippet: jump to its next / previous blank to fill in |

`Enter` and `Tab` don't accept: `Enter` starts a new line and `Tab` inserts a
tab, as if the menu weren't there. Keep typing to narrow the list down.

### Where suggestions come from

| Source | What it suggests | When |
|---|---|---|
| Language server | Variables, functions, fields, keywords, imports | Files whose language server is running (see Code above) |
| Snippets | Code templates with blanks, such as a function call with its arguments | When the language server offers them |
| Paths | File and directory names | After typing `/` or `./` |
| Neovim's Lua API | `vim.*` functions | Editing the Neovim config |

The menu labels each item with its kind (Function, Variable, Snippet and so
on). Accepting a function often fills in its arguments as a snippet: type the
first one, press `Ctrl+l` to jump to the next, and so on. Some language servers
also add the missing `#include` or import when you accept.

### Files without a language server

YAML, JSON, Markdown and plain text have no language server here, so the menu
only shows paths. Python has none without Node.js. For words already in your
open files, use Vim's built-in completion:

| Keys | What it does |
|---|---|
| `Ctrl+n` / `Ctrl+p` (with no menu showing) | Complete the word from open files |
| `Ctrl+x` then `Ctrl+l` | Complete the whole line |
| `Ctrl+x` then `Ctrl+f` | Complete a file name |

## Editing extras

| Keys | What it does |
|---|---|
| `s` `a` `i` `w` `)` | Surround the word with `()` (add) |
| `s` `d` `'` | Delete surrounding `'` |
| `s` `r` `)` `'` | Replace surrounding `)` with `'` |
| `v` `a` `q` / `c` `i` `q` | Select around / change inside any quotes |
| `v` `i` `a` | Select inside a function argument |
| `g` `c` `c` | Toggle comment on the line (`g` `c` in visual mode) |
| `Esc` | Clear search highlight |

## Windows and terminal

| Keys | What it does |
|---|---|
| `Ctrl+h` `j` `k` `l` | Move between splits |
| `:vsplit` / `:split` | Split vertically / horizontally |
| `:terminal` | Open a terminal; `Esc` `Esc` leaves terminal mode |

## Git

Changed lines are marked in the left column (gitsigns). `:Gitsigns
preview_hunk` shows the change under the cursor, `:Gitsigns blame_line` who
changed it.

## Debugging

| Keys | What it does |
|---|---|
| `Space` `b` | Toggle breakpoint |
| `Space` `B` | Conditional breakpoint |
| `F5` | Start / continue |
| `F1` / `F2` / `F3` | Step into / over / out |
| `F7` | Show / hide the debug UI |

## Commands

| Command | What it does |
|---|---|
| `:Lazy` | Plugin status |
| `:Mason` | Language servers and tools |
| `:checkhealth` | Diagnose problems |
| `:Tutor` | Built-in Vim tutorial |

`:Lazy update`, `:Mason` installs and new treesitter parsers need internet.
On a machine installed from the bundle, update them by installing a new bundle.
