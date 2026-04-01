---
icon: lucide/star
---

# Apex

## Chezmoi

```zsh
# Initialize and optionally pull from GitHub user
# ~/.local/share/chezmoi/
chezmoi init Az-21

# Apply from dotfiles repo to system
chezmoi apply

# Save to dotfiles repo
chezmoi add ~/.config/some-config-file

# Save to dotfiles repo (overwrite)
chezmoi re-add ~/.config/some-config-file

# Diff between system and dotfiles repo
chezmoi diff
```

## Mise

```zsh
# Upgrade all tools
mise upgrade

# Remove tools which are no longer listed in ~/.config/mise/config.toml
mise prune
```
