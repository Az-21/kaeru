## PATH
### Add to User PATH
```ps
[System.Environment]::SetEnvironmentVariable("Path", $env:Path + ";full/path/here", [System.EnvironmentVariableTarget]::User)
```

> [!NOTE]
> Semicolon before full path is required.

### Add to System PATH
This requires elevated shell.
```ps
[System.Environment]::SetEnvironmentVariable("Path", $env:Path + ";full/path/here", [System.EnvironmentVariableTarget]::Machine)
```
