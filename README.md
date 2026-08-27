# dotfiles

Personal dotfiles repository for this macOS machine (zsh, with bash
configs kept for compatibility). It tracks shell startup files such as
PATH setup so a fresh shell or a new machine can be configured
consistently, without exposing the rest of the home directory.

## Layout

This repository is rooted at `$HOME`. To keep the rest of the home
directory (secrets, caches, nested project repos) out of git, `.gitignore`
ignores everything by default and whitelists only the files below:

- `.zshrc` — interactive zsh configuration
- `.zprofile` — zsh login shell configuration (PATH setup, Homebrew shellenv)
- `.bashrc` — interactive bash configuration
- `.bash_profile` — bash login shell configuration

## Installing on a new machine

This repo is rooted at `$HOME` itself rather than a separate directory
with symlinks, so setup means initializing `$HOME` as a git checkout of
it.

1. Back up any existing files that would be overwritten (`.zshrc`,
   `.zprofile`, `.bashrc`, `.bash_profile`):
   ```
   mkdir -p ~/dotfiles-backup
   cp ~/.zshrc ~/.zprofile ~/.bashrc ~/.bash_profile ~/dotfiles-backup/ 2>/dev/null
   ```
2. Initialize `$HOME` as a git repo and pull this repo's history into it:
   ```
   cd ~
   git init -b main
   git remote add origin git@github.com:cmong67/dotfiles.git
   git fetch origin
   git checkout -f main
   ```
   `checkout -f` overwrites any tracked files already present, which is
   why step 1 matters. Untracked files elsewhere in `$HOME` are left
   alone.
3. Open a new shell (or `source ~/.zprofile`) to pick up the configuration.

## Daily usage

Treat `$HOME` as the working tree for this repo:

```
cd ~
git status
git add .zshrc            # or whichever tracked file you edited
git commit -m "Update zshrc"
git push
```

## Adding a new file to track

Add an explicit negation entry to `.gitignore`, e.g.:

```
!/.some_new_config
```

then `git add .some_new_config` as usual.
