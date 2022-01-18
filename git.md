# git

## unstage

Unstage specific file:  
`git restore --staged <file>`  
Unstage everything but keep changes: `git reset`

---

_DO NOT_ carelessly use commands `rebase` or `filter-repo`

---

## filter-repo

Only filter-repo on a mirror clone:  
`git clone --mirror git@github.com:user/repo.git`

## erase untracked (deleted) files from history

Get a list of deleted files still in commit history:  
`git log --diff-filter=D --summary`  
Filter a particular file or dir:  
`git filter-repo --invert-paths --path my_file.png --path my_path/src/*`  
Filter a list of files, dirs, etc:  
`git filter-repo --invert-paths --paths-from-file my_list.txt`

## mailmap

Update entire repo's commits' author/email:  
`git filter-repo --mailmap ~/.mailmap --force`  
Content of .mailmap:  
`newAuthor <new@email.foo> oldAuthor <old@email.foo>`

## rebase

Only rebase on a clone of said mirror: `git clone mirrored_repo.git`  
Edit a particular commit: `git rebase -i commit_after_particular`  
or:  
`git rebase -i 664724d5119c302567082110d201d06b20f31099`

Edit a list of commits:  
`git rebase -i HEAD~42`  
or:  
`git rebase -i --root`

## sign your commits

Sign your commit: `git commit -S -m "commit message"`  
Easy way to sign all previous commits:  
`git rebase --exec 'git commit --amend --no-edit -n -S' -i --root`

Get list of commits with signatures:  
`git log --show-signature`  
or:  
`git log --pretty="format:%h %G? %aN %s"`

## remote

```bash
git remote add origin https://github.com/dj-mc/ket.git
git remote -v
git push --set-upstream origin master
```
