### Move Files One Level Up
```powershell
Get-ChildItem -Path . -Directory | ForEach-Object { Get-ChildItem -Path $_.FullName | Move-Item -Destination . }
```

### Move Files One Level Up > Delete Empty Folders
```powershell
Get-ChildItem -Path . -Directory | ForEach-Object { Get-ChildItem -Path $_.FullName | Move-Item -Destination .; Remove-Item -LiteralPath $_.FullName }
```
