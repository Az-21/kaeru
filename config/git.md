## Local Project Config
```sh
git config user.name "John Doe"
git config user.email "john.doe@domain.com"
git config user.signingkey A000000000000000
```

> [!NOTE]
> GitHub enables a private email to hide your email. Prefer to use that email to hide your real email.
> 
> It can be found in Settings > Emails.

## Global Project Config
```sh
# Just add a --global flag
git config --global user.name "John Doe"
git config --global commit.gpgsign true
```

## View Config
```sh
git config --get user.email
git config --get --global user.email
```
