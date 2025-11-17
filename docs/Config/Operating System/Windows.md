# Windows
## Initial Setup
```powershell
winget upgrade --all
```

```powershell
winget install `
  Git.Git `
  GitHub.GitHubDesktop `
  M2Team.NanaZip `
  Microsoft.PowerShell `
  Microsoft.PowerToys `
  Microsoft.VisualStudio.2022.Community `
  Microsoft.VisualStudioCode `
  Neovim.Neovim `
  Starship.Starship `
  Typst.Typst `
  Valve.Steam `
  ajeetdsouza.zoxide `
  astral-sh.uv `
  jdx.mise `
  junegunn.fzf `
```

[Get Dotfiles](https://github.com/Az-21/dotfiles){ .md-button .md-button--primary }

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
