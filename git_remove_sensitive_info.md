
## archive uncommitted modified files
```
git status --porcelain | grep '^ M ' | cut -d " " -f3 | xargs zip update.zip
```

## How to delete sensitive info from git & github
If you commit sensitive info in git/github, please follow below steps to delete from history forever: (Backup your source file first!!!)

1. delete related info from code.
2. reset code version head, NOT index.
```
## if you wanna revert head to initial status, plz remove .git and init it again
git reset --soft Head~1
git add .
git commit -m "remove something...:)"
```

3. replace remote repo by creating a `temp` repo.

```
git checkout -b temp
git push origin temp:temp

##switch your default repo as 'temp' in your github setting, otherwise next step would fail
git push origin --delete master
git checkout master git push origin master:master

##switch default repo from temp to master in your github setting
git branch -d temp
```
if you use github desktop client, please delete this project and add it.
Note: If you have anything issue or question, please leave me message in this repo
