# Contributing

This is a personal dotfiles repository, rooted at `$HOME` on a single
machine. It isn't intended to accept outside contributions, but the
guidelines below keep changes consistent if you're revisiting this later
or adapting it for another machine.

## Making changes

1. Edit the tracked file directly in `$HOME` (e.g. `~/.zshrc`).
2. Review the diff before committing:
   ```
   cd ~
   git diff -- .zshrc
   ```
3. Commit with a short, descriptive message:
   ```
   git add .zshrc
   git commit -m "Describe the change"
   git push
   ```

## Tracking a new file

By default, `.gitignore` ignores everything in `$HOME` except the files
explicitly whitelisted in it. To track a new file:

1. Add a negation entry to `.gitignore`, e.g. `!/.some_new_config`.
2. `git add .some_new_config`, commit, and push.

Never remove the leading `/*` ignore-everything rule in `.gitignore` —
it's what keeps secrets, caches, and unrelated project directories out
of this repository.

## Guidelines

- Keep secrets (API keys, tokens, passwords) out of tracked files. Use
  environment-specific, untracked files or a secret manager instead.
- Prefer small, focused commits with a clear message describing the
  shell behavior being changed.
- Test changes in a new shell session before pushing, to catch syntax
  errors in startup files early.
