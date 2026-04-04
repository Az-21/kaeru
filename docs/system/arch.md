---
icon: simple/archlinux
---

# Arch

## Initial Setup

```zsh
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
yay -Y --gendb && yay -Syu --devel && yay -Y --devel --save
```

```zsh
yay -S --needed \
  aur/github-desktop-plus-bin \
  aur/microsoft-edge-beta-bin \
  aur/microsoft-edge-stable-bin \
  core/curl \
  extra/code \
  extra/git \
  extra/ksshaskpass \
  extra/kwallet-pam \
  extra/mise \
  extra/unzip \
  extra/wezterm \
  extra/wget \
  extra/zed \
  extra/zsh \
  extra/zsh-autosuggestions \
  extra/zsh-syntax-highlighting

chsh -s $(which zsh)
```

```
yay && mise upgrade
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

### SSH

!!! abstract

    Hooking into KDE’s systemd boot process, we can ensure that SSH agent starts on boot, uses login password to unlock the SSH key, and makes it available globally to both terminal and GUI apps.

```zsh
systemctl --user enable --now ssh-agent.service
```

```zsh
mkdir -p ~/.config/environment.d
nano ~/.config/environment.d/ssh.conf
```

```plaintext title="~/.config/environment.d/ssh.conf"
SSH_AUTH_SOCK="${XDG_RUNTIME_DIR}/ssh-agent.socket"
SSH_ASKPASS="/usr/bin/ksshaskpass"
SSH_ASKPASS_REQUIRE="prefer"
```

```zsh
mkdir -p ~/.local/bin
nano ~/.local/bin/ssh-add-kwallet.sh
```

```plaintext title="~/.local/bin/ssh-add-kwallet.sh"
#!/bin/bash
ssh-add ~/.ssh/id_ed25519 < /dev/null
```

!!! warning

    `ssh-add ~/.ssh/id_ed25519` is just an example. Ensure you have added the correct SSH key.

```zsh
chmod +x ~/.local/bin/ssh-add-kwallet.sh
```

All the script and files are now configured. Now, we need to add the script to autostart.

1. KDE System Settings > Autostart
2. Add > Add Login Script
3. Browse to and select `~/.local/bin/ssh-add-kwallet.sh`.
