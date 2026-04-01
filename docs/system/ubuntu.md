---
icon: simple/ubuntu
---

# Ubuntu

## Initial Setup

```zsh
sudo apt update && sudo apt upgrade && sudo apt install nala
```

```zsh
sudo nala install \
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
sudo curl https://gpg.polrivero.com/public.key | sudo gpg --dearmor -o /usr/share/keyrings/polrivero.gpg
echo "deb [arch=amd64,arm64 signed-by=/usr/share/keyrings/polrivero.gpg] https://deb.github-desktop.polrivero.com/ stable main" | sudo tee /etc/apt/sources.list.d/github-desktop-plus.list
sudo nala update && sudo nala install github-desktop-plus

# VS Code Editor
curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /etc/apt/keyrings/microsoft.gpg > /dev/null
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/microsoft.gpg] https://packages.microsoft.com/repos/code stable main" | sudo tee /etc/apt/sources.list.d/vscode.list
sudo nala update && sudo nala install code

# Switch to new soruce list format
sudo apt modernize-sources
```

```zsh
sudo nala update && sudo nala upgrade && sudo nala autoremove && mise upgrade
```

## Dotfiles

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
