# Debian
## Initial Setup
```bash
sudo apt update
sudo apt upgrade

# Dependencies
sudo apt install curl wget git

# Starship.rs
curl -sS https://starship.rs/install.sh | sh

# Python -> uv package manager
wget -qO- https://astral.sh/uv/install.sh | sh
```

## Bash Profile
```bash
#.bashrc > Append

# Starship
eval "$(starship init bash)"
```

## Input Profile
```bash
# ~/.inputrc > Replace
$include /etc/inputrc
"\e[A":history-search-backward
"\e[B":history-search-forward

set colored-stats On
set completion-ignore-case On
set completion-prefix-display-length 3
set mark-symlinked-directories On
set show-all-if-ambiguous On
set show-all-if-unmodified On
set visible-stats On
```

## WSL
### GitHub Desktop
Use this as the local path when cloning a repo.
```bash
# \\wsl.localhost\{DISTRO}\home\{User}\Code\{Orgnization}\{Repo}
\\wsl.localhost\Debian\home\Az21\Code\Az-21\{Repo}
```

!!! tip "Windows `git` vs Linux `git`"

    GitHub Desktop uses the `git` from Windows. To make local (repo level) changes to fields like user name, user email, and signing key, run the git command using `git.exe`.

    ```bash
    # ~/some-repo
    git.exe config --local user.email
    ```

[Get Dotfiles](https://github.com/Az-21/dotfiles){ .md-button .md-button--primary }
