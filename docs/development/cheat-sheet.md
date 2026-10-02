---
icon: lucide/file-code-corner
---

# Cheat Sheet

## Move Files

### Move Files One Level Up

```nu
let moves = (ls | where type == dir | each { |dir| ls $dir.name | get name } | flatten); $moves | each { |file| {action: "move", path: $file} } | print; if (input --default "n" "Proceed? [y/N] " | str lowercase) == "y" { $moves | each { |file| mv $file . } | ignore }
```

### Move Files One Level Up `&&` Delete Empty Folders

```nu
let dirs = (ls | where type == dir | get name); let moves = ($dirs | each { |dir| ls $dir | get name } | flatten); $moves | each { |file| {action: "move", path: $file} } | print; $dirs | each { |dir| {action: "remove", path: $dir} } | print; if (input --default "n" "Proceed? [y/N] " | str lowercase) == "y" { $moves | each { |file| mv $file . } | ignore; $dirs | each { |dir| if (ls -a $dir | is-empty) { rm $dir } } | ignore }
```
