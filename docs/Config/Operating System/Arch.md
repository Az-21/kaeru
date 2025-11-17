# Arch
## Initial Setup
```bash
pacman -Syu

# Install yay
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay-bin.git && cd yay-bin && makepkg -si
```

```bash
# Upgrade all
yay

# Install
yay -S uv starship mise

# Cleanup
yay -Yc
```

[Get Dotfiles](https://github.com/Az-21/dotfiles){ .md-button .md-button--primary }
