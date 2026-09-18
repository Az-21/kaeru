---
icon: lucide/boxes
---

# Mise

```zsh
# Global tool usage
mise use --global tool@latest

# Local tool usage (`cd` into project first)
mise use tool@24

# Upgrade all tools
mise upgrade

# Upgrade all tools bypassing release age safety
mise upgrade --minimum-release-age=0s

# Remove tools which are no longer listed in ~/.config/mise/config.toml and older releases
mise prune

# Auto-approve prune
mise prune -y
```

```zsh
mise upgrade --minimum-release-age=0s && mise prune -y
```
