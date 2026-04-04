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

## Git

```zsh
# Private, non-tracked gitignore
vi .git/info/exclude
```

```zsh
# Skip tracking of already commited files
git update-index --assume-unchanged {file}
```

## Mise

```zsh
# Common dev tools (unpinned)
mise use --global tool@latest

# Upgrade all tools
mise upgrade

# Remove tools which are no longer listed in ~/.config/mise/config.toml
mise prune

# Pinned version (local)
# cd into project to create a project specific mise.toml | Mise automatically switches on cd
mise use node@20
```
