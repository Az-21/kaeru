---
icon: simple/apple
---

# macOS

## Initial Setup

```zsh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

```zsh
brew install \
  git \
  mise \
  zsh-autosuggestions \
  zsh-syntax-highlighting

brew install --cask \
  steam \
  visual-studio-code \
  wezterm \
  zed

brew install \
  pol-rivero/tap/github-desktop-plus
```

```zsh
brew update && brew upgrade --greedy && brew upgrade --cask --greedy && brew cleanup && mise upgrade
```

## Dotfiles

!!! tip

    Run `mise doctor` and fix any issues before running the following commands.

```zsh
mise use -g chezmoi@latest
chezmoi init Az-21
chezmoi apply
mise upgrade
```
