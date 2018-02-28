### How to merge multiple commit
[Original Article][ref1]

Suppose you want to merge last 4 commits
```
$ git rebase -i HEAD~4
```
In the text editor that comes up, replace the words "pick" with "squash" next to the commits you want to squash into the commit before it. Save and close the editor, and git will combine the "squash"'ed commits with the one before it. Git will then give you the opportunity to change your commit message to something like, "Issue #100: Fixed retweet bug."

Push into your github, use --force if you've already pushed
```
$ git push origin branch-name --force
```

**Tips**:   
You can always edit your last commit message, before pushing, by using:
```
$ git commit --amend
```

### How to merge specific files from other branch
1. git checkout *branch-you-want-to-merge-to*
2. git cherry-pick *branch-you-want-to-merge-from*
__maybe you need solve code conflict here__
3. git RESET HEAD   // To make all files untracked
4. git add *files-you-want-to-merge*
5. git commit -m "merge from xxxx"

Good Luck!

[ref1]: https://github.com/todotxt/todo.txt-android/wiki/Squash-All-Commits-Related-to-a-Single-Issue-into-a-Single-Commit "Squash All Commits Into Single Commit"
