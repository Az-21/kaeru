# Setting Up Multiple Git Accounts
## Key Generation
### SSH Directory / Workspace
```sh
# Create SSH workspace
cd ~ # Equivalent to current user in Windows
mkdir .ssh
cd .ssh
```

### SSH Key Generation
```sh
# Create SSH key
ssh-keygen - t ed25519 -C "email@domain.com" -f "output-key-name"
```

### SSH Config
```sh
# Create config file
touch config
```
```
# ~/.ssh/config

# Git Account #1
Host github.com-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/account-1-key

# Git Account #2
Host github.com-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/account-2-key
```

### Known Host
```
# Create known host file
touch known_hosts
```
```
# ~/.ssh/known_hosts
# Add known hosts here
```

- Google XYZ's SSH key fingerprints to get public key fingerprints
- GitHub: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints

## Clone
```sh
# Normal SSH clone
git clone git@github.com:Az-21/kaeru.git

# Profile/account specific clone
git clone git@github.com-personal:Az-21/kaeru.git
#                        ^ This will configure with personal profile (account#1)

git clone git@github.com-work:Az-21/kaeru.git
#                        ^ This will configure with work profile (account#2)
```

### Username and Email
```sh
cd <repo>
git config user.name "username"
git config user.email "email@domain.com" # Consider using email alias (GitHub: Setting > Access > Emails)
```
