# test-signing-commit

Hello here.

On windows, I installed https://www.gpg4win.org/index.html

1. Create a new GPG key pair: `gpg --gen-key`
2. Get keyid from `gpg --list-secret-keys --keyid-format LONG`
3. `git config --global user.signingkey B64A4B8D241577B8`
4. `git config --global user.signingkey B64A4B8D241577B8`
5. Commit with *-S* flag: `git commit -S -m "message"`
