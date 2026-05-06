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
  wez.wezterm `
  ZedIndustries.Zed
```

```powershell
winget upgrade --all && mise upgrade
```

## Dotfiles

!!! tip

    Run `mise doctor` and fix any issues before running the following commands.

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

## Misc

### WSL

#### GitHub Desktop

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

### Taskbar Apps

!!! abstract

    This section is for work computers where IT has applied a auto-set taskbar apps group policy.

1. Pin the apps you want and unpin unnecessary apps before starting.
2. `cd "~/AppData/Roaming/Microsoft/Internet Explorer/Quick Launch/User Pinned/TaskBar"`
3. Note the names of the `.lnk` links in this folder.
4. `cd ~/AppData/Local/Microsoft/Windows/Shell`.
5. Create `LayoutModification.xml` if it does not exist and use the following template as starting point.

```xml title="LayoutModification.xml" hl_lines="12-14"
<?xml version="1.0" encoding="utf-8"?>
<LayoutModificationTemplate
    xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"
    xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout"
    xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout"
    xmlns:taskbar="http://schemas.microsoft.com/Start/2014/TaskbarLayout"
    Version="1">

    <CustomTaskbarLayoutCollection PinListPlacement="Replace">
        <defaultlayout:TaskbarLayout>
            <taskbar:TaskbarPinList>
                <!-- Add your pinned apps here -->
                <taskbar:DesktopApp DesktopApplicationLinkPath="%APPDATA%\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar\YOUR-FIRST-APP.lnk" />
                <taskbar:DesktopApp DesktopApplicationLinkPath="%APPDATA%\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar\YOUR-SECOND-APP.lnk" />
            </taskbar:TaskbarPinList>
        </defaultlayout:TaskbarLayout>
    </CustomTaskbarLayoutCollection>

</LayoutModificationTemplate>
```
