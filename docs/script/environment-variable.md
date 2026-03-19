---
icon: lucide/terminal
---

# Environment Variables

## PowerShell (Windows)

### Add a New Variable

**User Variable:**

```powershell
[System.Environment]::SetEnvironmentVariable("VAR_NAME", "Value", [System.EnvironmentVariableTarget]::User)
```

**System Variable (Requires Admin):**

```powershell
[System.Environment]::SetEnvironmentVariable("VAR_NAME", "Value", [System.EnvironmentVariableTarget]::Machine)
```

### Add to PATH

PowerShell doesn't have a built-in cmdlet to safely append to the `PATH` without manually dealing with semicolons. The safest approach is to create a reusable function (you can add this to your `$PROFILE`) that automatically manages the semicolons and prevents duplicate entries.

```powershell
function Add-Path {
    param(
        [Parameter(Mandatory=$true)]
        [string]$NewPath,
        [System.EnvironmentVariableTarget]$Scope = [System.EnvironmentVariableTarget]::User
    )

    $current = [System.Environment]::GetEnvironmentVariable("Path", $Scope)
    $updatedParts = ($current -split ';' | Where-Object { $_ }) + $NewPath | Select-Object -Unique
    [System.Environment]::SetEnvironmentVariable("Path", ($updatedParts -join ';'), $Scope)
}
```

```powershell
Add-Path -NewPath "C:\full\path\here"
```

```powershell
Add-Path -NewPath "C:\full\path\here" -Scope Machine
```
