---
icon: lucide/git-branch
---

# Git

## Initial Setup

### Local Project Config

```sh
git config --local user.name "John Doe"
git config --local user.email "john.doe@domain.com"
git config --local user.signingkey A000000000000000
```

!!! note

    GitHub enables a private email to hide your email. Prefer to use that email to hide your real email.

    It can be found in Settings > Emails.

### Global Project Config

```sh
git config --global user.name "John Doe"
git config --global commit.gpgsign true
```

### View Config

```sh
git config --get user.email
git config --get --global user.email
```
