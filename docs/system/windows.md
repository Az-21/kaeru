---
icon: lucide/monitor
---

# Windows

## Initial Setup

```powershell
winget upgrade --all
```

```powershell
winget install `
  ajeetdsouza.zoxide `
  astral-sh.uv `
  Atuinsh.Atuin `
  BurntSushi.ripgrep.MSVC `
  eza-community.eza `
  Git.Git `
  GitHub.GitHubDesktop `
  junegunn.fzf `
  M2Team.NanaZip `
  Microsoft.PowerShell `
  Microsoft.PowerToys `
  Microsoft.VisualStudio.Community `
  Microsoft.VisualStudioCode `
  Neovim.Neovim `
  Schniz.fnm `
  sharkdp.bat `
  sharkdp.fd `
  Starship.Starship `
  jqlang.jq `
  sxyazi.yazi `
  tbillington.kondo `
  twpayne.chezmoi `
  Typst.Typst `
  wez.wezterm `
  ZedIndustries.Zed
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
