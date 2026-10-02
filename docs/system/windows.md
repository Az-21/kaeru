---
icon: lucide/monitor
---

# Windows

## Upgrade All

```sh title="Admin"
winget upgrade --all
```

```sh
mise upgrade --minimum-release-age=0s; mise prune -y
```

```sh
# :: powershell
mise upgrade --minimum-release-age=0s && mise prune -y
```

---

## Initial Setup

```sh
winget upgrade --all
```

```sh
# :: powershell
winget install Nushell.Nushell
```

!!! tip

    Start Nushell using `nu` from the default terminal for now. It will be later set as the default shell on WezTerm via dotfiles.

```sh
winget install ...[
  DesktopPlus.DesktopPlus
  Git.Git
  jdx.mise
  M2Team.NanaZip
  Microsoft.PowerShell
  Microsoft.PowerToys
  Microsoft.VisualStudio.BuildTools
  wez.wezterm
  ZedIndustries.Zed
]
```

## Dotfiles

[:lucide-bolt: Initialize dotfiles](../development/chezmoi.md)

## SSH Setup

```sh
# :: powershell
# Run on startup
Get-Service ssh-agent | Set-Service -StartupType Automatic
```

```sh
# :: powershell
# Start in current run (one-time, won't need after restarting once)
Start-Service ssh-agent
```

```sh
# :: powershell
# Verify
Get-Service ssh-agent
```

```sh
# :: powershell
# Use Windows SSH client
if ($sshPath = (Get-Command ssh -ErrorAction SilentlyContinue).Source) { [System.Environment]::SetEnvironmentVariable("GIT_SSH_COMMAND", ($sshPath -replace '\\', '/'), [System.EnvironmentVariableTarget]::User); Write-Host "[ OK ] $sshPath is now the default SSH client" -ForegroundColor Green; Write-Host "NOTE: Restart terminal/apps for changes to take effect." -ForegroundColor Yellow } else { Write-Host "Error: ssh not found" -ForegroundColor Red }
```

```sh
# :: powershell
# Confirm default SSH client after restating terminal/app
[System.Environment]::GetEnvironmentVariable("GIT_SSH_COMMAND", [System.EnvironmentVariableTarget]::User)
```

## Misc

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
