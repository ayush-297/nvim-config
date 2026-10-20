# Neovim keybindings

Quick reference for this config. **Leader is `Space`**, so `<leader>ff` means `Space f f`.

## General

| Keys | Mode | Action |
|---|---|---|
| `jk` | insert | Exit insert mode |
| `<leader>nh` | normal | Clear search highlights |

## Windows (splits)

| Keys | Action |
|---|---|
| `<leader>sv` | Split vertically |
| `<leader>sh` | Split horizontally |
| `<leader>se` | Make splits equal size |
| `<leader>sx` | Close current split |
| `<leader>sm` | Maximize / restore current split |
| `Ctrl + h / j / k / l` | Move to split left / down / up / right (vim-tmux-navigator) |

## Tabs

| Keys | Action |
|---|---|
| `<leader>to` | New tab |
| `<leader>tx` | Close tab |
| `<leader>tn` / `<leader>tp` | Next / previous tab |
| `<leader>tf` | Open current file in a new tab |

## File explorer (nvim-tree)

| Keys | Action |
|---|---|
| `<leader>ee` | Toggle explorer |
| `<leader>ef` | Toggle explorer on the current file |
| `<leader>ec` | Collapse all folders |
| `<leader>er` | Refresh |

Inside the explorer (plugin defaults):

| Keys | Action |
|---|---|
| `Enter` / `o` | Open file / expand folder |
| `Ctrl+v` / `Ctrl+x` / `Ctrl+t` | Open in vertical split / horizontal split / new tab |
| `a` | Create file (end with `/` for a folder) |
| `r` | Rename |
| `d` | Delete |
| `x` / `c` / `p` | Cut / copy / paste |
| `y` / `Y` / `gy` | Copy name / relative path / absolute path |
| `-` | Go up one directory |
| `H` / `I` | Toggle dotfiles / git-ignored files |
| `g?` | Show all explorer keys |

## Find (Telescope)

| Keys | Action |
|---|---|
| `<leader>ff` | Find files |
| `<leader>fr` | Recent files |
| `<leader>fs` | Search text in project (live grep) |
| `<leader>fc` | Search word under cursor |
| `<leader>ft` | Find TODO comments |

Inside the picker:

| Keys | Action |
|---|---|
| `Ctrl+j` / `Ctrl+k` | Next / previous result |
| `Enter` | Open |
| `Ctrl+v` / `Ctrl+x` / `Ctrl+t` | Open in vertical split / horizontal split / new tab |
| `Ctrl+q` | Send results to the quickfix list |
| `Esc` | Normal mode in picker (press again to close) |

## LSP (when a language server is attached)

| Keys | Action |
|---|---|
| `gd` | Go to definition |
| `gD` | Go to declaration |
| `gR` | Show references |
| `gi` | Show implementations |
| `gt` | Show type definitions (overrides "next tab" in these buffers) |
| `K` | Hover documentation |
| `<leader>ca` | Code actions (also on a visual selection) |
| `<leader>rn` | Rename symbol |
| `<leader>d` | Diagnostics for current line |
| `<leader>D` | Diagnostics for current file |
| `[d` / `]d` | Previous / next diagnostic |
| `<leader>rs` | Restart LSP |

## Completion (insert mode, nvim-cmp)

| Keys | Action |
|---|---|
| `Ctrl+Space` | Show suggestions |
| `Ctrl+j` / `Ctrl+k` | Next / previous suggestion |
| `Enter` | Accept selected suggestion |
| `Ctrl+e` | Close menu |
| `Ctrl+b` / `Ctrl+f` | Scroll documentation |

Brackets and quotes close automatically (nvim-autopairs).

## Editing

| Keys | Action |
|---|---|
| `gcc` | Toggle comment on line |
| `gc` + motion / `gc` in visual | Toggle comment on range |
| `ys` + motion + char | Surround, e.g. `ysiw"` wraps word in quotes |
| `ds` + char | Delete surrounding, e.g. `ds"` |
| `cs` + old + new | Change surrounding, e.g. `cs"'` |
| `<leader>r` + motion | Replace motion with yanked text |
| `<leader>rr` | Replace line with yanked text |
| `<leader>R` | Replace to end of line with yanked text |
| `<leader>r` (visual) | Replace selection with yanked text |
| `Ctrl+Space` (normal) | Start / expand selection by syntax node |
| `Backspace` (visual) | Shrink syntax selection |

## Formatting & linting

| Keys | Action |
|---|---|
| (on save) | Format automatically (prettier, stylua, isort + black) |
| `<leader>mp` | Format file, or selection in visual mode |
| `<leader>l` | Run linter (pylint for Python) |

## Git (gitsigns)

| Keys | Action |
|---|---|
| `]h` / `[h` | Next / previous hunk |
| `<leader>hs` / `<leader>hr` | Stage / reset hunk (also on visual selection) |
| `<leader>hS` / `<leader>hR` | Stage / reset whole buffer |
| `<leader>hu` | Undo last stage |
| `<leader>hp` | Preview hunk |
| `<leader>hb` | Blame line (full) |
| `<leader>hB` | Toggle inline blame |
| `<leader>hd` / `<leader>hD` | Diff against index / last commit |
| `ih` | Text object for the hunk (e.g. `vih`, `dih`) |

## TODOs & sessions

| Keys | Action |
|---|---|
| `]t` / `[t` | Next / previous TODO comment |
| `<leader>ws` | Save session for current directory |
| `<leader>wr` | Restore session for current directory |

## Start screen

`e` new file · `SPC ee` explorer · `SPC ff` find file · `SPC fs` find word · `SPC wr` restore session · `q` quit

## Known quirks

- **Inside tmux, `Ctrl+j` is the tmux prefix**, so it never reaches Neovim: moving to the split below and `Ctrl+j` in completion/Telescope lists don't work there. Use the arrow keys in lists.
- **`<leader>r` waits ~1s** before acting, because `<leader>rn`, `<leader>rr` and `<leader>rs` also start with it.
- **`signcolumn` is off** (second block in `core/options.lua` overrides the first), so git and diagnostic signs in the gutter don't show.
