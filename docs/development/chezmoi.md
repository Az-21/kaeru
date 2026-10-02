---
icon: lucide/folder-sync
---

# Chezmoi

## Use `Az-21` Dotfiles

!!! note

    Run `mise doctor` and fix any issues before running the following commands.

```sh
mise use -g chezmoi@latest
chezmoi init Az-21
chezmoi apply
mise upgrade
```

!!! tip

    Once system is fully configured, switch to SSH auth for chezmoi folder.

    ```sh
    z (chezmoi source-path)
    git remote set-url origin git@github.com:Az-21/dotfiles.git
    ```

## General Usage

```sh
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
