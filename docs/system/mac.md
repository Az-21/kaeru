---
icon: simple/apple
---

# macOS

## Upgrade All

```sh
brew update; brew upgrade --greedy; brew upgrade --cask --greedy; brew cleanup; mise upgrade --minimum-release-age=0s; mise prune -y
```

```sh
# :: zsh
brew update && brew upgrade --greedy && brew upgrade --cask --greedy && brew cleanup && mise upgrade --minimum-release-age=0s && mise prune -y
```

---

## Initial Setup

!!! important

    Install [brew](https://brew.sh/)

```sh
# :: zsh
brew install \
  desktop-plus/tap/desktop-plus \
  git \
  mise \
  nushell

brew install --cask \
  wezterm \
  zed
```

## Dotfiles

[:lucide-bolt: Initialize dotfiles](../development/chezmoi.md)
