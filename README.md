# test-signing-commit

Hello here changes again.

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

> I did not manage to get this work on Windows so I set an empty passphrase... with `gpg --edit-key <PASTE_YOUR_KEY_ID_HERE>` then `passwd` and finally `save`


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

**I also had a problem because GIT comes with its own version of GPG (v1.4.21) but GnuPG4Win comes with another version (v2.2.3)**
To solve this problem, I check that in my ENVIRONMENT VARIABLE, *GnuPG/bin* comes **before** *git/bin* to force the use of same version (the one from GnuPG4Win).
