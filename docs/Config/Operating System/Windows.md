# Windows
## Initial Setup
```powershell
winget upgrade --all
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
New-Alias dl yt-dlp               # YouTube Downloader

# Enable Starship.rs
Invoke-Expression (&starship init powershell)
```