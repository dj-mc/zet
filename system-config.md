# system-config

## etckeeper

Open `sudo gedit /etc/etckeeper/etckeeper.conf`  
Uncomment `AVOID_DAILY_AUTOCOMMITS=1`

```bash
sudo etckeeper vcs log /etc/
sudo etckeeper vcs status
sudo etckeeper vcs diff
sudo etckeeper commit "Added changes"
```

## cron

todo

## systemd

todo

## gpg

<https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification>

`gpg --full-generate-key`

```bash
gpg --armor --export B8BF1574863DCAB0
gpg --output public.pgp --armor --export 49037253+dj-mc@users.noreply.github.com
gpg --output private.pgp --armor --export-secret-key 49037253+dj-mc@users.noreply.github.com
```

or: `gpg --armor --export EMAIL_ADDRESS > public_key.asc`

Import private key:
`gpg --import private.pgp`
Public key (optional, no reason to?):
`gpg --import public.pgp`

Upload to keys.gnupg.net public key server (optional).

`gpg --list-keys`
`gpg --send-keys PRIMARY_ID`
Import someone else's
`gpg --import PUBLIC_KEY`

## ssh

```bash
ls -al ~/.ssh
cat ~/.ssh/id_ed25519
eval "$(ssh-agent -s)"
```

If needed: `exec ssh-agent bash`  
Add your key: `ssh-add ~/.ssh/id_ed25519`  
or: `ssh-add -k ~/.ssh/id_ed25519`  

<https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh>

```bash
ssh-keygen -t ed25519 -C "49037253+dj-mc@users.noreply.github.com"
eval "$(ssh-agent -s)"
clip < ~/.ssh/id_ed25519.pub
ssh -T git@github.com
```

## gh-cli

`brew install gh`  
`brew upgrade gh`
