---
icon: lucide/scroll-text
---

# Transformation

## Move

### Move Files One Level Up

=== "PowerShell"

    ```powershell
    Get-ChildItem -Path . -Directory | ForEach-Object { Get-ChildItem -Path $_.FullName | Move-Item -Destination . }
    ```

=== "Zsh"

    ```zsh
    setopt dotglob nullglob; for dir in */; do [ -d "$dir" ] && mv -- "$dir"* . 2>/dev/null; done; unsetopt dotglob nullglob
    ```

=== "Bash"

    ```bash
    shopt -s dotglob nullglob; for dir in */; do [ -d "$dir" ] && mv -- "$dir"* . 2>/dev/null; done; shopt -u dotglob nullglob
    ```

### Move Files One Level Up > Delete Empty Folders

=== "PowerShell"

    ```powershell
    Get-ChildItem -Path . -Directory | ForEach-Object { Get-ChildItem -Path $_.FullName | Move-Item -Destination .; Remove-Item -LiteralPath $_.FullName }
    ```

=== "Zsh"

    ```zsh
    setopt dotglob nullglob; for dir in */; do [ -d "$dir" ] && mv -- "$dir"* . 2>/dev/null && rmdir -- "$dir"; done; unsetopt dotglob nullglob
    ```

=== "Bash"

    ```bash
    shopt -s dotglob nullglob; for dir in */; do [ -d "$dir" ] && mv -- "$dir"* . 2>/dev/null && rmdir -- "$dir"; done; shopt -u dotglob nullglob
    ```
