---
icon: lucide/terminal
---

# Environment Variables

## Linux

!!! abstract

    Most modern Linux distributions use `Systemd` and it's environment variables become accessible to both terminal and GUI apps. Ensure your system uses it before proceeding.

### User

```ini title="~/.config/environment.d/user-variables.conf"
MY_VAR_1=value1
MY_VAR_2=value2
```

!!! tip "Applying Changes"

    Changes in `environment.d` require you to log out and log back in, or restart the user systemd instance.

### System

```ini title="/etc/environment"
MY_SYS_VAR_1=value1
MY_SYS_VAR_2=value2
```

## Windows

### Add a New Variable

```powershell title="User variable"
[System.Environment]::SetEnvironmentVariable("VAR_NAME", "Value", [System.EnvironmentVariableTarget]::User)
```

```powershell title="System variable"
[System.Environment]::SetEnvironmentVariable("VAR_NAME", "Value", [System.EnvironmentVariableTarget]::Machine)
```

### Add to PATH

PowerShell does not have a built-in `cmdlet` to safely append to the `PATH` without manually managing semicolons. The safest approach is to create a reusable function.

!!! example "Profile Setup"

    Add the following function to your `$PROFILE` so it is always available in your PowerShell sessions.

    ```powershell
    function Add-Path {
        param(
            [Parameter(Mandatory=$true)]
            [string]$NewPath,
            [System.EnvironmentVariableTarget]$Scope = [System.EnvironmentVariableTarget]::User
        )
        $current = [System.Environment]::GetEnvironmentVariable("Path", $Scope)
        $updatedParts = ($current -split ';' | Where-Object { $_ }) + $NewPath
        $seen = [System.Collections.Generic.HashSet[string]]::new([System.StringComparer]::OrdinalIgnoreCase)
        $deduped = $updatedParts | Where-Object { $seen.Add($_) }
        [System.Environment]::SetEnvironmentVariable("Path", ($deduped -join ';'), $Scope)
    }
    ```

    !!! example "Usage"

        ```powershell
        Add-Path -NewPath "C:\full\path\here" -Scope User
        ```

        ```powershell
        Add-Path -NewPath "C:\full\path\here" -Scope Machine
        ```
