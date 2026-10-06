# Cheatsheets

Quick reference for the things I look up often, and an index of where the
longer notes actually live.

This repo is deliberately thin. It holds **TL;DR tables** for the things I
reach for daily — tiling window managers, Neovim and yazi — and otherwise it is an
**index**: pointers to documentation in my other repos, plus a few canonical
external references per topic. Notes live next to the thing they describe. This
page tells you which repo to open.

🔒 marks a private repo — the link will 404 unless you are me.

---

## TL;DR — Tiling window managers

Three window managers, one on each OS. The configs live in
[dotfiles](https://github.com/zrrbite/dotfiles); the full per-WM documentation
is linked under each column.

**All three now share `hjkl`. Only the modifier differs** — `SUPER` on Linux,
`alt` on the other two.

| Intent | Hyprland (Linux) | AeroSpace (macOS) | GlazeWM (Windows) |
|---|---|---|---|
| **Modifier** | `SUPER` | `alt` (Option) | `alt` |
| Focus left/down/up/right | `SUPER`+`h/j/k/l` or arrows | `alt`+`h/j/k/l` | `alt`+`h/j/k/l` or arrows |
| Move window in direction | `SUPER-shift`+`h/j/k/l` or arrows | `alt-shift`+`h/j/k/l` | `alt-shift`+`h/j/k/l` or arrows |
| Cycle focus | — | `alt-tab` | `alt-space` |
| Workspace N | `SUPER`+`1`–`0` | `alt`+`1`–`9` | `alt`+`1`–`9` |
| Send window to workspace N | `SUPER-SHIFT`+N *(stays)* | `alt-shift`+N *(follows)* | `alt-shift`+N *(follows)* |
| Next / previous workspace | `SUPER`+scroll | `alt-s` / `alt-a` | `alt-s` / `alt-a` |
| Back and forth | — | `alt-d` | `alt-d` |
| Workspace → other monitor | — | `alt-shift-a` / `-f` | `alt-shift-a` / `-f` / `-d` / `-s` |
| Close window | `SUPER-C` | `alt-shift-q` | `alt-shift-q` |
| Fullscreen | — | `alt-f` | `alt-f` |
| Toggle floating | `SUPER-V` | `alt-shift-space` | `alt-shift-space` |
| Tiling direction | `SUPER-T` | `alt-v` | `alt-v` |
| Resize width − / + | `SUPER`+`=` *(1080² only)* | `alt-u` / `alt-p` | `alt-u` / `alt-p` |
| Resize height − / + | — | `alt-i` / `alt-o` | `alt-i` / `alt-o` |
| Resize mode | — | `alt-r` | *disabled — reserved for PowerToys Run* |
| Terminal | `SUPER-Q` | `alt-enter` | `alt-enter` |
| App launcher | `SUPER-R` | — *(Spotlight)* | `alt-r` *(PowerToys Run)* |
| Reload config | — | `alt-shift-r` | `alt-shift-r` |
| Lock the screen | `SUPER-CTRL-L` | `⌃⌘Q` *(macOS)* | *(Win+L)* |
| Exit the WM | `SUPER-M` *(no confirm)* | — | `alt-shift-e` |
| In-app cheatsheet | `SUPER-F1` | — | `alt-F12` |

A dash means nothing is bound for that intent.

**Why Hyprland keeps a different modifier:** its config sets
`kb_options = grp:alt_shift_toggle`, so **Alt+Shift** cycles between the Danish
and US keyboard layouts. That is exactly the chord the other two use for moving
windows, so `alt` is not available there. The `hjkl` bindings had no such
excuse — they were missing entirely until 2026-07-26, a leftover from the stock
config, and are now bound to match. Adding them moved `togglesplit` to
`SUPER-T` and the lock screen to `SUPER-CTRL-L`.

The configs are authoritative; this table is a convenience copy. When they
disagree, the config wins — and on Hyprland, `SUPER-F1` reads the live bindings
straight from `hyprctl`.

**Full documentation**

- [Cross-platform comparison](https://github.com/zrrbite/dotfiles/blob/master/doc/tiling-window-managers.md)
- [Hyprland](https://github.com/zrrbite/dotfiles/blob/master/doc/hyprland.md) — dwindle layout, screenshots, why it diverges
- [AeroSpace](https://github.com/zrrbite/dotfiles/blob/master/doc/aerospace-macos.md) — the accordion trap, restarts losing placement, focus-follows-mouse
- [GlazeWM](https://github.com/zrrbite/dotfiles/blob/master/doc/glazewm.md) — window rules for Office and games, zebar
- [Status bar theming](https://github.com/zrrbite/dotfiles/blob/master/doc/status-bar-theming.md) — waybar and sketchybar

**Canonical references**

- [Hyprland wiki](https://wiki.hypr.land/)
- [AeroSpace guide](https://nikitabobko.github.io/AeroSpace/guide)
- [GlazeWM](https://github.com/glzr-io/glazewm) · [zebar](https://github.com/glzr-io/zebar)

---

## TL;DR — Neovim

Leader is `Space`. Config in
[dotfiles/nvim](https://github.com/zrrbite/dotfiles/tree/master/nvim).

**Find — Telescope**

| Key | Action |
|---|---|
| `<leader>ff` | Find files |
| `<leader>fg` | Live grep |
| `<leader>fb` | Buffers |
| `<leader>fs` | Symbols in this file |
| `<leader>fw` | Symbols across the workspace |
| `<leader>fd` | Diagnostics |
| `<leader>fh` | Help tags |
| `<leader>fm` | Macros (`#define`) |

**LSP**

| Key | Action |
|---|---|
| `gd` / `gD` | Go to definition / declaration |
| `gr` / `gI` | References / implementations |
| `K` | Hover documentation |
| `<leader>rn` | Rename symbol |
| `<leader>ca` | Code action |
| `<leader>D` | Type definition |
| `<leader>sh` | Signature help |
| `<leader>F` | Format |

**C++ (clangd only)**

| Key | Action |
|---|---|
| `<leader>h` | Switch header ↔ source |
| `<leader>cf` | Batch fix with `clang-tidy --fix` |

**Diagnostics**

| Key | Action |
|---|---|
| `<leader>d` | Show diagnostic at cursor, floating |
| `<leader>q` | All diagnostics in the location list |
| `]d` / `[d` | Next / previous diagnostic |

**Debug — DAP**

| Key | Action |
|---|---|
| `F5` | Start / continue |
| `F10` / `F11` / `F12` | Step over / into / out |
| `<leader>b` / `<leader>B` | Toggle breakpoint / conditional breakpoint |
| `<leader>du` | Toggle the debug UI |
| `<leader>dr` / `<leader>dl` | Open REPL / run last |

**Windows and files**

| Key | Action |
|---|---|
| `<leader>e` | Toggle file tree (neo-tree) |
| `C-h/j/k/l` | Move between splits |
| `C-w` `v` / `s` / `q` | Split vertical / horizontal / close |
| `<leader>mp` | Markdown preview (glow) |
| `Esc` | Clear search highlight |

Two things that catch me out: `<leader>d` (diagnostic float) shares a prefix
with `<leader>du`/`<leader>dr`, so it waits for `timeoutlen` before firing. And
`<leader>F` formats while `<leader>f` opens Telescope — same letter, different
case, different world.

On Linux, `SUPER-F3` pops this list up in rofi.

**Full documentation**

- [nvim-tutorial.md](https://github.com/zrrbite/dotfiles/blob/master/doc/nvim-tutorial.md) — a seven-level walkthrough from motions to macros, with exercises
- [vscode.md](https://github.com/zrrbite/dotfiles/blob/master/doc/vscode.md) — VS Code defaults, for when I am not in nvim

**Canonical references**

- [Neovim docs](https://neovim.io/doc/) · [vimhelp.org](https://vimhelp.org/) (searchable `:help`)
- [lazy.nvim](https://lazy.folke.io/) · [Telescope](https://github.com/nvim-telescope/telescope.nvim)
- [VS Code keybindings](https://code.visualstudio.com/docs/getstarted/keybindings)

---

## TL;DR — yazi (terminal file manager)

The Finder replacement, on macOS and Arch. Launch with **`y`**: quitting with
`q` leaves your shell in the folder you browsed to. Plain `yazi` doesn't.
Config in [dotfiles/yazi](https://github.com/zrrbite/dotfiles/tree/master/yazi).
Keys are checked against yazi 26.9's own keymap, and **`~` inside yazi lists
them all**.

**Move**

| Key | Action |
|---|---|
| `h` / `l` | Up to the parent folder / into a folder |
| `j` / `k` | Down / up |
| `gg` / `G` | Top / bottom |
| `Ctrl-d` / `Ctrl-u` | Half a page down / up |
| `H` / `L` | Back / forward through folders you've visited |
| `z` / `Z` | Jump anywhere: fuzzy (fzf) / frecent (zoxide) |

**Act on files**

| Key | Action |
|---|---|
| `Enter` / `o` | Open with the default app (`O`: choose the app) |
| `Space` / `v` | Select / visual range select (`Esc` clears) |
| `Ctrl-a` / `Ctrl-r` | Select all / invert the selection |
| `y` / `x` / `p` | Copy / cut / paste (`P` overwrites, `Y` cancels) |
| **`d`** / **`D`** | **Move to Trash** / **delete permanently** |
| `r` | Rename (several selected: bulk rename in your editor) |
| `a` | Create a file; end the name with `/` for a folder |
| `-` / `_` | Symlink the copied files: absolute / relative path |

**Find and view**

| Key | Action |
|---|---|
| `s` / `S` | Search names (fd) / search contents (ripgrep) |
| `f` | Filter the current folder |
| `/` | Find the next match by name |
| `.` | Show / hide hidden files |
| `Tab` | Details of the hovered file |
| `J` / `K` | Scroll the preview |
| `,` then `m` / `e` / `a` / `n` | Sort by modified / extension / A–Z / natural (capital letter = reverse) |
| `m` then `s` / `p` / `m` | Show size / permissions / modified time beside each name |

**Copy a path, run a command, tabs**

| Key | Action |
|---|---|
| `c` then `c` / `d` / `f` / `n` | Copy file path / folder path / filename / filename without extension |
| `;` / `:` | Run a shell command here (`:` waits for it to finish) |
| `t` `t` / `1`–`9` | New tab / switch tab (`t` `r` renames it, `Ctrl-c` closes it) |
| `w` | Running tasks (copies and moves in progress) |
| `q` | Quit (`Q`: quit and stay where you started) |

Image previews are real images in Ghostty, including inside tmux, and coloured
blocks elsewhere. For a quick look without yazi: `chafa image.jpg`, or `fimg` to
fuzzy-find and preview the images below the current folder.

**Full documentation**

- [dotfiles README, yazi and chafa](https://github.com/zrrbite/dotfiles#yazi---modern-file-manager)

**Canonical references**

- [yazi docs](https://yazi-rs.github.io/docs/quick-start) · [default keymap](https://github.com/sxyazi/yazi/blob/main/yazi-config/preset/keymap-default.toml)

---

## Index

### Tooling

**Desktop and dotfiles**

- [dotfiles](https://github.com/zrrbite/dotfiles) — Nord-themed, Stow-managed, Arch + macOS + Windows + WSL. Install scripts per platform.
- [archinstall](https://github.com/zrrbite/archinstall) — Arch installation guide and notes.
- [Arch wiki](https://wiki.archlinux.org/) · [GNU Stow manual](https://www.gnu.org/software/stow/manual/stow.html) · [Omarchy](https://omarchy.org/)

**C++**

- cpp-resources 🔒 — articles, books, notes and projects.
- [lumen](https://github.com/zrrbite/lumen) — embedded GUI framework for Cortex-M0 to M7.
- [forge-compiler](https://github.com/zrrbite/forge-compiler) — a compiler experiment in Rust.
- [cppreference](https://en.cppreference.com/) · [Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) · [Compiler Explorer](https://godbolt.org/) · [quick-bench](https://quick-bench.com/)

**Agentic coding**

- [agentic](https://github.com/zrrbite/agentic) — notes on Claude Code extensibility, alternatives, integrations.
- committool 🔒 — hook-gated commits and an on-demand analysis runner (Node + Effect-TS).
- [Claude Code docs](https://docs.claude.com/en/docs/claude-code) · [Model Context Protocol](https://modelcontextprotocol.io/)

**Embedded and graphics**

- touchgfx-hw 🔒 — LTDC, DSI, SPI, DMA2D, framebuffers, panels.
- touchgfx-rpi 🔒 — TouchGFX 4.26.1 on Raspberry Pi, SDL2 and DRM/KMS.
- [TouchGFX docs](https://support.touchgfx.com/docs/introduction/welcome) · [libusb API](https://libusb.sourceforge.io/api-1.0/)

### Not tooling

**Coffee roasting**

- libbullet 🔒 — C/C++ library for the Aillio Bullet R1 over libusb.
- bullet-ble 🔒 — Raspberry Pi BLE-to-USB bridge.
- bullet-ios 🔒 — the phone app.
- ble-protocol 🔒 — canonical wire protocol shared by Pi, STM32 and iOS.

**Photography**

- leicaq2 🔒 — Leica Q2 field notes, Capture One workflow, and the photo archive checklists. The one to open before a trip and after a card dump.
- [Capture One](https://www.captureone.com/) · [Leica](https://leica-camera.com/)

**Fermentation and brewing**

- [yeastlab](https://github.com/zrrbite/yeastlab) — sourdough (Double Enzymatic Activation), baker's yeast bread, and beer. Same enzymes, same microbes, different staging.
- [perferments](https://github.com/zrrbite/perferments) — fermentation write-ups in TeX.
- [doughy](https://github.com/zrrbite/doughy) — Raspberry Pi fermentation temperature controller.
- [tilt-hydrometer-analysis](https://github.com/zrrbite/tilt-hydrometer-analysis) — fermentation logging from a Tilt.
- [The Fresh Loaf](https://www.thefreshloaf.com/) · [Brewer's Friend](https://www.brewersfriend.com/)

**Home and outdoors**

- [husquarna-automow](https://github.com/zrrbite/husquarna-automow) — Automower parts, error codes, maintenance. Primary model: 310.

**Puzzles and games**

- aoc 🔒 — Advent of Code in C++.
- [claude-codes-aoc](https://github.com/zrrbite/claude-codes-aoc) — Advent of Code, but Claude drives.
- [valheim-gate](https://github.com/zrrbite/valheim-gate) — teleport to your bind spot or anywhere on the map.

---

## Conventions

- Notes live in the repo they describe. This page indexes; it does not copy.
- The TL;DR tables are the deliberate exception, kept to *intents* rather
  than exhaustive binding lists. The config always wins. Add one only for
  something used daily.
- External links are capped at a handful per topic. This is not a bookmark
  dump.
