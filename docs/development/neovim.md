---
icon: simple/neovim
---

# Neovim

## Installation

```sh
mise use -g neovim@latest
```

## Astrovim

```sh title="Reset Neovim"
rm -rf ~/.local/share/nvim
rm -rf ~/.local/state/nvim
rm -rf ~/.cache/nvim
rm -rf ~/.config/nvim
```

```sh title="Install Astrovim"
git clone --depth 1 https://github.com/AstroNvim/template ~/.config/nvim
```
