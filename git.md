# git

`git branch -r`
`git fetch --prune`
`git clone --mirror` vs. `git clone --bare`
`git fetch` vs. `git pull`

## clean

Remove untracked files: `git clean -d -n`

## unstage

Unstage specific file:  
`git restore --staged <file>`  
Unstage everything but keep changes: `git reset`

## discard uncommitted

```bash
git stash
git stash drop
```

## undo last commit

`git reset HEAD~`  
Split the initial commit (while rebasing), but there is no HEAD.
Instead: `git update-ref -d HEAD` then `git rm --cached -r .`
``

## amend last commit

Edit commit message + content:  
*Stage new changes before amending*  
`git commit --amend`  
If you only need to edit commit content:  
`git commit --amend --no-edit`

## stash local, pull remote, unstash local (pop)

```bash
git stash
git pull
git stash pop
```

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

Edit a particular commit: `git rebase -i commit_AFTER_particular`  
e.g. `git rebase -i 664724d5119c302567082110d201d06b20f31099`

Rebase a range:  
`git rebase -i HEAD~42`  
Rebase all commits:  
`git rebase -i --root`

## gpg signature

Sign a commit:  
`git commit -S -m "commit message"`  
Sign all commits:  
`git rebase --exec 'git commit --amend --no-edit -n -S' -i --root`

## git log

Get list of last 3 commits:  
`git log --pretty=format:"%h %s" HEAD~3..HEAD`  
Get list of commits and their signatures:  
`git log --show-signature`  
Signatures prettified (G/E/N):  
`git log --pretty="format:%h %G? %aN %s"`

## remote

```bash
git remote add origin https://github.com/dj-mc/ket.git
git remote -v
git push --set-upstream origin master
```
