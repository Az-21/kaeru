---
icon: simple/archlinux
---

# Arch

## Upgrade All

```sh
yay; mise upgrade --minimum-release-age=0s; mise prune -y
```

```sh
# :: bash
yay && mise upgrade --minimum-release-age=0s && mise prune -y
```

---

## Initial Setup

!!! note

    This guide is intended for -- and assumes -- Arch KDE with `plasma-meta` as base.

!!! tip

    For a better starting experience, install the following apps **during** `archinstall`.

    - `extra/chromium`
    - `extra/wezterm`
    - `extra/nushell`

    This guide goes over installing these regardless, this is just a time saver.

!!! important

    Install [yay](https://github.com/Jguer/yay/blob/next/README.md)

```sh
# :: bash
yay -S --needed extra/nushell
```

!!! tip

    Start Nushell using `nu` from the default terminal for now. It will be later set as the default shell on WezTerm via dotfiles.

```sh
yay -S --needed ...[
  aur/desktop-plus-bin
  aur/microsoft-edge-stable-bin
  core/curl
  extra/ark
  extra/chromium
  extra/dolphin
  extra/git
  extra/gwenview
  extra/ksshaskpass
  extra/kwallet-pam
  extra/mise
  extra/spectacle
  extra/unzip
  extra/wezterm
  extra/wget
  extra/zed
]
```

## Dotfiles

[:lucide-bolt: Initialize dotfiles](../development/chezmoi.md)

### SSH

!!! abstract

    Hooking into KDE’s systemd boot process, we can ensure that SSH agent starts on boot, uses login password to unlock the SSH key, and makes it available globally to both terminal and GUI apps.

```sh
systemctl --user enable --now ssh-agent.service
```

```sh
mkdir ~/.config/environment.d
nano ~/.config/environment.d/ssh.conf
```

```ini title="~/.config/environment.d/ssh.conf"
SSH_AUTH_SOCK="${XDG_RUNTIME_DIR}/ssh-agent.socket"
SSH_ASKPASS="/usr/bin/ksshaskpass"
SSH_ASKPASS_REQUIRE="prefer"
```

```sh
mkdir ~/.local/bin
nano ~/.local/bin/ssh-add-kwallet.sh
```

```sh title="~/.local/bin/ssh-add-kwallet.sh"
#!/bin/bash
ssh-add ~/.ssh/id_ed25519 < /dev/null
```

!!! warning

    `ssh-add ~/.ssh/id_ed25519` is just an example. Ensure you have added the correct SSH key.

```sh
chmod +x ~/.local/bin/ssh-add-kwallet.sh
```

All the script and files are now configured. Now, we need to add the script to autostart.

1. KDE System Settings > Autostart
2. Add > Add Login Script
3. Browse to and select `~/.local/bin/ssh-add-kwallet.sh`.

## Indexing

!!! abstract

    To keep system snappy, I prefer to tone down the indexing. Following instructions are for KDE.

    1. Search "File Search" in Application Launcher (Start Menu)
    2. Change data to index option to "File names only"
    3. Add an exclusion for the development folder (e.g., `~/Dev`)
