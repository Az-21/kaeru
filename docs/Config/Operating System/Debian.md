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
eval "$(starship init bash)"
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