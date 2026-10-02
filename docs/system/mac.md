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
brew install nushell
```

!!! tip

    Start Nushell using `nu` from the default terminal for now. It will be later set as the default shell on WezTerm via dotfiles.

```sh
brew install ...[
  desktop-plus/tap/desktop-plus
  git
  mise
]

brew install --cask ...[
  wezterm
  zed
]
```

## Dotfiles

[:lucide-bolt: Initialize dotfiles](../development/chezmoi.md)
