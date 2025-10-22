# Windows
## Initial Setup
```powershell
winget upgrade --all

winget install Microsoft.PowerToys Microsoft.PowerShell Starship.Starship Valve.Steam Typst.Typst Git.Git GitHub.GitHubDesktop Neovim.Neovim Microsoft.VisualStudio.2022.Community Microsoft.VisualStudioCode CoreyButler.NVMforWindows astral-sh.uv M2Team.NanaZip
```

## PowerShell Profile
```powershell
# Create and open PS profile
code $PROFILE
```
```powershell
# Alias first party tools and commands
New-Alias e Explorer              # Open explorer
New-Alias hash Get-FileHash       # Generate SHA256 hash
New-Alias touch New-Item          # Create new, empty file

# Alias third party tools and commands
New-Alias vi nvim                 # NeoVim
New-Alias vim nvim                # NeoVim

# Enable Starship.rs
Invoke-Expression (&starship init powershell)
```