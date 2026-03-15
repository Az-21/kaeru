---
icon: lucide/apple
---
# macOS
## Initial Setup
```zsh
# Install brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
```zsh
brew install \
  `# Shell history sync and search across machines via a database` \
  atuin \
  `# cat replacement with syntax highlighting and git integration` \
  bat \
  `# ls replacement with icons, git status, and tree view` \
  eza \
  `# find replacement — faster, simpler, and .gitignore-aware` \
  fd \
  `# Fast Node.js version manager written in Rust` \
  fnm \
  `# Fuzzy finder for shell history, files, and more` \
  fzf \
  `# Distributed version control system` \
  git \
  `# JSON processor and query tool for the command line` \
  jq \
  `# Reclaims disk space by cleaning build artifacts (node_modules, target, etc.)` \
  kondo \
  `# Hyperextensible Vim-based text editor` \
  neovim \
  `# grep replacement — fast recursive search with regex support` \
  ripgrep \
  `# Cross-shell prompt customizer` \
  starship \
  `# Modern typesetting system (LaTeX alternative)` \
  typst \
  `# Fast Python package and project manager (pip/venv replacement)` \
  uv \
  `# Terminal file manager with image preview` \
  yazi \
  `# Smarter cd — jumps to frecent directories` \
  zoxide

brew install --cask \
  `# GUI client for GitHub repositories` \
  github \
  `# PC gaming platform and store` \
  steam \
  `# Lightweight extensible code editor` \
  visual-studio-code \
  `# GPU-accelerated terminal emulator with Lua config` \
  wezterm \
  `# Fast GPU-accelerated collaborative code editor` \
  zed
```


```zsh
brew update && brew upgrade --greedy && brew upgrade --cask --greedy && brew cleanup
```

[Get Dotfiles](https://github.com/Az-21/dotfiles){ .md-button .md-button--primary }
