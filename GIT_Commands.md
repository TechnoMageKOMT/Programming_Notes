# Git Essentials  

### Creating and Setting up a new repository (repo)  

Create a new repo on GitHub and give it a name in the required field
Create a directory for a git project:
```
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
### Push requests  

After creating a new file or changes it is unstaged.

`~$ git status`
```
`git add first-push.txt` To stage the new file.       Staging
`git commit -m "First is the first official commit"`  Commit
`git push origin main`                                 push  

An origin is where the remote code is being sent to or saved or hosted.
```
  ~$ git remote -v
```
Will list all the origins like the following example:

### Branching
```
git checkout -b new-branch
```
Creates a new branch and switches to the new branch.
```
git branch
```
List branches and also an * next to current branch.
```
   main
* new-branch
```
```
git checkout main
```
Switches back to the main branch.  

The idea is to create "small" and then merging them with the main branch if and when suitable. **NOT** to create extensive very large branches which defeats the purpose of version control.

**Committing to a new branch**

Simply change to new branch with the `git checkout <new-branch>` command, add a file and then go through the push cycle. Once done, there will be a "Compare & pull request" on Github called a pull request.

### Merging a branch into main

Merging is the act of taking one branch and applying it to another branch.  

```
~$ git checkout main    (To change to main branch )
~$ git pull origin main (Update any changes on main from github and apply to local file(s))(I.e., update local)
~$ git merge <new-branch>
~$ git push origin main (Push changes to Github)
```

### Git log

`~$ git log~`

Log of times, comments and usernames for changes.

### Git fetch

```
~$ git fetch origin main
~$ git log --oneline --graph --decorate --all   (Refer alias: glg)
```

```
`~$ git diff <filename>`
```
This will list the differences applied to a file before staging it. It only works before the file is staged.