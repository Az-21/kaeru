# macOS
## Initial Setup
```zsh
# Install brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
```zsh
brew install \
  atuin \               # Shell history sync and search across machines via a database
  bat \                 # cat replacement with syntax highlighting and git integration
  eza \                 # ls replacement with icons, git status, and tree view
  fd \                  # find replacement — faster, simpler, and .gitignore-aware
  fnm \                 # Fast Node.js version manager written in Rust
  fzf \                 # Fuzzy finder for shell history, files, and more
  git \                 # Distributed version control system
  jq \                  # JSON processor and query tool for the command line
  kondo \               # Reclaims disk space by cleaning build artifacts (node_modules, target, etc.)
  neovim \              # Hyperextensible Vim-based text editor
  ripgrep \             # grep replacement — fast recursive search with regex support
  starship \            # Cross-shell prompt customizer
  typst \               # Modern typesetting system (LaTeX alternative)
  uv \                  # Fast Python package and project manager (pip/venv replacement)
  yazi \                # Terminal file manager with image preview
  zoxide                # Smarter cd — jumps to frecent directories

brew install --cask \
  github \              # GUI client for GitHub repositories
  steam \               # PC gaming platform and store
  visual-studio-code \  # Lightweight extensible code editor
  wezterm \             # GPU-accelerated terminal emulator with Lua config
  zed                   # Fast GPU-accelerated collaborative code editor
```


```zsh
brew update && brew upgrade --greedy && brew upgrade --cask --greedy && brew cleanup
```

[Get Dotfiles](https://github.com/Az-21/dotfiles){ .md-button .md-button--primary }
