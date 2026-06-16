# Cheat Sheet

## Git + RipGrep Selective Search

1. Get the files affected by a commit.
2. Run `ripgrep` on these files.

```zsh
git diff-tree --no-commit-id -r --name-only -z {{commit-hash}} | xargs -0 rg "search-term"
```
