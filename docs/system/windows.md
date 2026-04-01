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
  Git.Git `
  jdx.mise `
  M2Team.NanaZip `
  Microsoft.PowerShell `
  Microsoft.PowerToys `
  Microsoft.VisualStudio.Community `
  Microsoft.VisualStudioCode `
  polrivero.GitHubDesktopPlus `
  Schniz.fnm `
  wez.wezterm `
  ZedIndustries.Zed
```

```powershell
winget upgrade --all && mise upgrade
```

## Dotfiles

```powershell
mise use -g chezmoi@latest
chezmoi init Az-21
chezmoi apply
mise upgrade
```

## SSH Setup

```powershell
# Run on startup
Get-Service ssh-agent | Set-Service -StartupType Automatic

# Start in current run (one-time, won't need after restarting once)
Start-Service ssh-agent

# Verify
Get-Service ssh-agent
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
