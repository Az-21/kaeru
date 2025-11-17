# Arch
## Initial Setup
```bash
sudo pacman -Syu

# Install yay
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay-bin.git && cd yay-bin && makepkg -si
```

```bash
yay -S \
  fzf \
  ghostty \
  github-desktop-bin \
  microsoft-edge-stable-bin \
  mise \
  starship \
  uv \
  visual-studio-code-bin \
  zoxide \
```

```bash
# Cleanup
yay -Yc
```

[Get Dotfiles](https://github.com/Az-21/dotfiles){ .md-button .md-button--primary }
