### Useful Git commands

To select which files to stage, highly recommend to use the "partial" flag:

```
git add -p
```

Then commit as usual before pushing:

```
git commit -m "A nice message"
git push origin main
```

(or replace main with the specific branch name above)

---

To undo a commit and everything which has been staged:

```
git reset HEAD^
```

---

To pull a specific file from another branch ("other-branch") to a specific branch (my-branch), first make sure your other branch is up to date locally:

```
git checkout other-branch
git pull origin other-branch
```

Then, switch back to the branch where you want to pull the file into, and pull the file:

```
git checkout my-branch
git checkout other-branch -- the-file-I-want
```

Hopefully it is obvious, but if not make sure to replace "my-branch", "other-branch", and "the-file-I-want" with the specific branch and file names for your case.
