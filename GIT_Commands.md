# Git Essentials  

## Creating and Setting up a new repository (repo)

Create a new repo on GitHub and give it a name in the required field
Create a directory for a git project:

```bash
1 ~$ mkdir test
2 ~$ cd test/
3 ~$ echo "# <repo name see above>" >> README.md
4 ~$ git init (Creates a git folder for Git "inner workings")
5 ~$ git add README.md (stage README.md file)
6 ~$ git commit -m "First commit"
7 ~$ git remote add origin git@github.com:TechnoMageKOMT/<repo name see above>.git
8 ~$ git push -u origin main
If (8) produces an src error 
  ~$ git branch -M main
  ~$ git push -u origin main
```

## Stage, Commit, Push (SCP) Cycle  

After creating a new file or changes it is unstaged.

`git status`
`git diff`  (To see the changes)

`git add <filename>` To stage the new file.           Staging
`git commit -m "First is the first official commit"`  Commit
`git push origin main`                                Push  

## Current Origin (I.e., which repo)

An origin is where the remote code is being sent to or saved or hosted.

```bash
  ~$ git remote -v
```

## Branching

Creates a new branch and switches to the new branch.

```bash
git checkout -b new-branch or
git branch new-branch
```

List branches and also an * next to current branch.

```bash
git branch
```

To switch between branches use the `checkout` command

```bash
git checkout main
```

The idea is to create "small" brances and/or commits then merging them with the main branch if and when suitable. **NOT** to create extensive very large branches which defeats the purpose of version control.

## Committing to a new branch

Simply change to new branch with the `git checkout <new-branch>` command, add a file and then go through the push cycle. Once done, there will be a "Compare & pull request" on Github called a pull request.

### Merging a branch into main

Merging is the act of taking one branch and applying it to another branch.  

```bash
~$ git checkout main    (To change to main branch )
~$ git pull origin main (Update any changes on main from github and apply to local file(s))(I.e., update local)
~$ git merge <new-branch>
~$ git push origin main (Push changes to Github)
```

### Git log

`~$ git log~`
`~$ git log --oneline`
`~$ glg` (alias created for graphical tree)
`~$ git diff <filename>`
    Filename not needed when only staging one file.

### Correcting bad commit messages

```bash
~$ git commit --amend
```

Will open nano where message can be changed. Must take place before push.

### How to stash code

Use case: Work done, not ready for commit, but needs to be saved "behind the scenes". This is a neat little temporary storage capability.

```bash
git stash   (To stash work)
git stash list  (To list all stashes on a branch)
git stash apply (When ready to resume)
git stash drop  (When ready to go through stage/commit/push cycle)
```

### Tags

This is mostly used for version control in software development.

```bash
git tag v0.1                        (To add tag)
git tag                             (To list all tags)
git push origin --tags              (To push the tag to GitHub)
git tag -d <tag name>               (To delete a tag)
git push origin --delete <tag name> (To delete tag from GitHub)
```
