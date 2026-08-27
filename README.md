# dotfiles

Shell configuration for this machine, tracked from `$HOME`.

## Layout

This repository is rooted at `$HOME`. To keep the rest of the home
directory (secrets, caches, nested project repos) out of git, `.gitignore`
ignores everything by default and whitelists only the files below:

- `.zshrc` — interactive zsh configuration
- `.zprofile` — zsh login shell configuration (PATH setup, Homebrew shellenv)
- `.bashrc` — interactive bash configuration
- `.bash_profile` — bash login shell configuration

## Adding a new file to track

Add an explicit negation entry to `.gitignore`, e.g.:

```
!/.some_new_config
```

then `git add .some_new_config` as usual.
