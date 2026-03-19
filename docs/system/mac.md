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
  bat \
  chezmoi \
  eza \
  fd \
  fnm \
  fzf \
  git \
  jq \
  kondo \
  neovim \
  ripgrep \
  starship \
  typst \
  uv \
  yazi \
  zoxide \
  zsh-autosuggestions \
  zsh-syntax-highlighting

brew install --cask \
  github \
  steam \
  visual-studio-code \
  wezterm \
  zed
```

```zsh
brew update && brew upgrade --greedy && brew upgrade --cask --greedy && brew cleanup
```
