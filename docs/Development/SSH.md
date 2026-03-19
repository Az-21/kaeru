---
icon: material/shield-key
---

# SSH

## Key Generation

```bash title="Generate a secure key"
ssh-keygen -t ed25519 -C "your_email@example.com" -f ~/.ssh/id_ed25519_personal
#          -t algo    -C comment (email)          -f filename
```

## Global Git Configuration

Organize your projects into subdirectories (e.g., `~/dev/personal` and `~/dev/work`) to trigger automatic identity switching.

```bash title="Prepare configuration directory"
mkdir --parents ~/.config/git/
```

### The Master Config (`~/.gitconfig`)

```ini title="~/.gitconfig"
[user]
    name = Default User
    email = default@email.com

[includeIf "gitdir:~/dev/personal/"]
    path = ~/.config/git/personal.gitconfig

[includeIf "gitdir:~/dev/work/"]
    path = ~/.config/git/work.gitconfig

[includeIf "gitdir:C:/dev/personal/"]
    path = ~/.config/git/personal.gitconfig
```

## Environment Overrides

The files inside `~/.config/git/` will override your global settings automatically.

=== "Personal (`~/.config/git/personal.gitconfig`)"

    ```ini
    [user]
        name = Personal Alias
        email = personal@email.com
        signingkey = ~/.ssh/id_ed25519_personal.pub
    [commit]
        gpgsign = true
    [gpg]
        format = ssh
    [core]
        sshCommand = "ssh -i ~/.ssh/id_ed25519_personal"
    ```

=== "Work (`~/.config/git/work.gitconfig`)"

    ```ini
    [user]
        name = Real Name
        email = employee@company.com
        signingkey = ~/.ssh/id_ed25519_work.pub
    [commit]
        gpgsign = true
    [gpg]
        format = ssh
    [core]
        sshCommand = "ssh -i ~/.ssh/id_ed25519_work"
    ```

## Verification

```bash title="Testing the setup"
cd ~/dev/work/my-project

# Verify identity
git config --get user.email
# Output: employee@company.com

# Verify SSH key usage
ssh -T git@github.com
# Output: Hi user! You've successfully authenticated...
```
