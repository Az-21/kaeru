---
icon: lucide/file-code-corner
---

# Cheat Sheet

## Move Files

### Move Files One Level Up

```sh
let files = (ls | where type == dir | get name | each { |dir| ls -a $dir | where type == file | get name } | flatten); let names = ($files | each { |f| $f | path basename }); let moves = ($files | each { |f| let n = ($f | path basename); {action: "move", current: $f, next: $n, conflict: (($n | path exists) or (($names | where { |x| $x == $n } | length) > 1))} }); $moves | print; if ($moves | any { |m| $m.conflict }) { print "Conflicts found, cancelled." } else if (input "Proceed? [y/N] " | str lowercase) == "y" { $moves | each { |m| mv $m.current . } | ignore }
```

### Move Files One Level Up `&&` Delete Empty Folders

```sh
let dirs = (ls | where type == dir | get name); let files = ($dirs | each { |dir| ls -a $dir | where type == file | get name } | flatten); let names = ($files | each { |f| $f | path basename }); let moves = ($files | each { |f| let n = ($f | path basename); {action: "move", current: $f, next: $n, conflict: (($n | path exists) or (($names | where { |x| $x == $n } | length) > 1))} }); let removes = ($dirs | each { |dir| {action: "remove", current: $dir, next: "(deleted if empty)", conflict: false} }); $moves | append $removes | print; if ($moves | any { |m| $m.conflict }) { print "Conflicts found, cancelled." } else if (input "Proceed? [y/N] " | str lowercase) == "y" { $moves | each { |m| mv $m.current . } | ignore; $dirs | each { |dir| if (ls -a $dir | is-empty) { rm $dir } } | ignore }
```
