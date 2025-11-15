# Scripts
## Move
### Move Files One Level Up
```powershell
# ps
Get-ChildItem -Path . -Directory | ForEach-Object { Get-ChildItem -Path $_.FullName | Move-Item -Destination . }
```
```bash
# bash
shopt -s dotglob nullglob; for dir in */; do [ -d "$dir" ] && mv -- "$dir"* . 2>/dev/null; done; shopt -u dotglob nullglob
```
```zsh
# zsh
setopt dotglob nullglob; for dir in */; do [ -d "$dir" ] && mv -- "$dir"* . 2>/dev/null; done; unsetopt dotglob nullglob
```

### Move Files One Level Up > Delete Empty Folders
```powershell
# ps
Get-ChildItem -Path . -Directory | ForEach-Object { Get-ChildItem -Path $_.FullName | Move-Item -Destination .; Remove-Item -LiteralPath $_.FullName }
```
```bash
# bash
shopt -s dotglob nullglob; for dir in */; do [ -d "$dir" ] && mv -- "$dir"* . 2>/dev/null && rmdir -- "$dir"; done; shopt -u dotglob nullglob
```
```zsh
# zsh
setopt dotglob nullglob; for dir in */; do [ -d "$dir" ] && mv -- "$dir"* . 2>/dev/null && rmdir -- "$dir"; done; unsetopt dotglob nullglob
```
