# test-signing-commit

Hello here .

On windows, I installed https://www.gpg4win.org/index.html

1. Create a new GPG key pair: `gpg --gen-key`
2. Get keyid from `gpg --list-secret-keys --keyid-format LONG`
3. `git config --global user.signingkey B64A4B8D241577B8`
4. `git config --global user.signingkey B64A4B8D241577B8`
5. Commit with *-S* flag: `git commit -S -m "message"`

To sign all commit by default (omit the *-S* flag), run `git config --global commit.gpgsign true`

To sign all tags by default (omit the *-s* flag), run `git config --global tag.gpgsign true`

## Import an existing GPG key
- `gpg --allow-secret-key-import --import github-sign-commit-private.key`
- `gpg --import github-sign-commit-pub-key.asc`

## Remember passphrase
Edit *~/.gnupg/gpg-agent.conf* and paste this content:

```
default-cache-ttl 28800
max-cache-ttl 28800
```
Edit *~/.gnupg/gpg.conf* and uncomment the line
```
use-agent
```

Restart the gpg-agent with `gpg-connect-agent reloadagent /bye`
