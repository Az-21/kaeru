# Git
## Initial Setup
### Local Project Config
```sh
git config user.name "John Doe"
git config user.email "john.doe@domain.com"
git config user.signingkey A000000000000000
```

> [!NOTE]
> GitHub enables a private email to hide your email. Prefer to use that email to hide your real email.
>
> It can be found in Settings > Emails.

### Global Project Config
```sh
# Just add a --global flag
git config --global user.name "John Doe"
git config --global commit.gpgsign true
```

### View Config
```sh
git config --get user.email
git config --get --global user.email
```

## Tracking Modifiers
### Ignore Locally
- Ignore locally without chaning `.gitignore` file.
- Useful when some files start showing up due to modified whitespace.
- Also useful for config files.

```sh
# Ignore locally
git update-index --assume-unchanged <file/folder>
```
```sh
# Start tracking again
git update-index --no-assume-unchanged <file/folder>
```

## Uses
### Diff Since Creation of Branch
```sh
git --no-pager diff --unified=0 main...HEAD
```
