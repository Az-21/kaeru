---
icon: simple/apple
---

# macOS

## Initial Setup

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

```sh
brew install \
  desktop-plus/tap/desktop-plus \
  git \
  mise \
  zsh-autosuggestions \
  zsh-syntax-highlighting

brew install --cask \
  wezterm \
  zed
```

```sh
brew update && brew upgrade --greedy && brew upgrade --cask --greedy && brew cleanup && mise upgrade --minimum-release-age=0s && mise prune -y
```

## Dotfiles

!!! tip

    Run `mise doctor` and fix any issues before running the following commands.

```sh
mise use -g chezmoi@latest
chezmoi init Az-21
chezmoi apply
mise upgrade
```
