---
icon: simple/ubuntu
---

# Ubuntu

!!! danger

    Ubuntu is absolute garbage. Package management situation is insane. It lacks core system utilities like clipboard history and screenshot markup. Canonical is still pushing Snap. GNOME is noticeably behind KDE.

## Initial Setup

```zsh
sudo apt update && sudo apt upgrade && sudo apt install nala
```

```zsh
sudo nala install \
  build-essential \
  curl \
  git \
  unzip \
  variety \
  wget \
  zsh \
  zsh-autosuggestions \
  zsh-syntax-highlighting

# Mise
sudo install -dm 755 /etc/apt/keyrings
curl -fSs https://mise.jdx.dev/gpg-key.pub | sudo tee /etc/apt/keyrings/mise-archive-keyring.asc 1> /dev/null
echo "deb [signed-by=/etc/apt/keyrings/mise-archive-keyring.asc] https://mise.jdx.dev/deb stable main" | sudo tee /etc/apt/sources.list.d/mise.list
sudo nala update && sudo nala install mise

# Wezterm
curl -fsSL https://apt.fury.io/wez/gpg.key | sudo gpg --yes --dearmor -o /etc/apt/keyrings/wezterm.gpg
echo 'deb [signed-by=/etc/apt/keyrings/wezterm.gpg] https://apt.fury.io/wez/ * *' | sudo tee /etc/apt/sources.list.d/wezterm.list
sudo nala update && sudo nala install wezterm

# Zsh Code Editor
curl -f https://zed.dev/install.sh | sh

# GitHub Desktop Plus
sudo curl https://gpg.desktop-plus.org/public.key | sudo gpg --dearmor -o /usr/share/keyrings/desktop-plus.gpg
echo "deb [arch=amd64,arm64 signed-by=/usr/share/keyrings/desktop-plus.gpg] https://apt.desktop-plus.org/ stable main" | sudo tee /etc/apt/sources.list.d/desktop-plus.list
sudo nala update && sudo nala install desktop-plus

# Switch to new soruce list format
sudo apt modernize-sources
```

```zsh
sudo nala update && sudo nala upgrade && sudo nala autoremove && mise upgrade
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

## Sane Configs

```zsh
# Center dock icons and trim for a macOS like dock
gsettings set org.gnome.shell.extensions.dash-to-dock extend-height false

# Make zsh default
chsh -s $(which zsh)
```
