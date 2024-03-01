# Terminal Config
## PowerShell Profile
```sh
# Alias first party tools and commands
New-Alias e Explorer              # Open explorer
New-Alias hash Get-FileHash       # Generate SHA256 hash
New-Alias touch New-Item          # Create new, empty file

# Alias third party tools and commands
New-Alias vi nvim                 # NeoVim
New-Alias vim nvim                # NeoVim
New-Alias dl yt-dlp               # YouTube Downloader

```

## LazyVim
```ps
# Find for telescope
winget install sharkdp.fd
```
```ps
# C compiler for treesitter | Add to src
https://github.com/mstorsjo/llvm-mingw/releases
```

## Theme
```json
{
  "name": "Monokai Remastered Kustom",
  "black": "#1a1a1a",
  "red": "#f4005f",
  "green": "#98e024",
  "yellow": "#98e024",
  "blue": "#9d65ff",
  "purple": "#f4005f",
  "cyan": "#58d1eb",
  "white": "#c4c5b5",
  "brightBlack": "#625e4c",
  "brightRed": "#f4005f",
  "brightGreen": "#98e024",
  "brightYellow": "#98e024",
  "brightBlue": "#9d65ff",
  "brightPurple": "#f4005f",
  "brightCyan": "#58d1eb",
  "brightWhite": "#f6f6ef",
  "background": "#0c0c0c",
  "foreground": "#d9d9d9",
  "selectionBackground": "#343434",
  "cursorColor": "#fc971f"
}
```
