# Generation
### Generate Key
```sh
gpg --full-generate-key
```

> [!TIP]
> Use the name on GitHub and the `@noreply` email provided by GitHub

### Get Keys
```sh
gpg --list-secret-keys --keyid-format=long
```

```c
sec   rsa4096/1XX1X11111000XX0 2016-07-01 [SC]
//            ^----Key ID----^ -> λ
      A123456AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
uid                 [ultimate] Octocat <octocat@github.com>
```

# Usage
### Sign Commits
```sh
git config --global user.signingkey λ
git config --global commit.gpgsign true
```

### Get Public Signature
```sh
# Windows PowerShell
gpg --export --armor λ | Set-Clipboard

# macOS (zsh or Bash)
gpg --export --armor λ | pbcopy
```

# Backup
### Create Backup
```
gpg --export --armor λ > GitHub-CommitSigningKey-Public.asc
gpg --export-secret-keys --armor λ > GitHub-CommitSigningKey-Private.asc
```

> [!NOTE]
> The exported secret key is still secure. It will require password (passphrase) before it can be imported and used.

### Import
```sh
gpg --import GitHub-CommitSigningKey-Private.asc
```
