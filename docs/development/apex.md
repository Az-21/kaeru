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
# Global tool usage
mise use --global tool@latest

# Local tool usage (`cd` into project first)
mise use tool@24

# Upgrade all tools
mise upgrade

# Upgrade all tools bypassing release age safety
mise upgrade --minimum-release-age=0s

# Remove tools which are no longer listed in ~/.config/mise/config.toml
mise prune
```
