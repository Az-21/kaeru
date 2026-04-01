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
curl -fsSL https://apt.fury.io/wez/gpg.key | sudo gpg --yes --dearmor -o /usr/share/keyrings/wezterm-fury.gpg
echo 'deb [signed-by=/usr/share/keyrings/wezterm-fury.gpg] https://apt.fury.io/wez/ * *' | sudo tee /etc/apt/sources.list.d/wezterm.list
sudo chmod 644 /usr/share/keyrings/wezterm-fury.gpg
sudo nala update && sudo nala install wezterm

# Zsh Code Editor
curl -f https://zed.dev/install.sh | sh

# VS Code Editor
sudo snap install code --classic

# Proton Pass CLI
curl -fsSL https://proton.me/download/pass-cli/install.sh | bash

# Switch to new soruce list format
sudo apt modernize-sources
```

```zsh
sudo nala update && sudo nala upgrade && mise upgrade
```
