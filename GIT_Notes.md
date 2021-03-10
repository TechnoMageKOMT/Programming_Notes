# Git Essentials  

CLI = Command Line Interface
GUI = Graphical User Interface  

When code needs to be deployed to a server there is no graphical user interface at all. For this fundamental reason it is better to learn git using the CLI.  

## Configuring GIT  

This is only done once unless the details changes.

```bash
git config -- global user.name "TechnoMageKOMT"  
git config -- global user.email "technomagekomt@gmail.com" (Email should ideally match up with GitHub email)  
cat ~/.gitconfig to verify that it worked.  
```

### SSH Key  

To generate SSH key:

```bash
ssh-keygen -o
```

To view key: cat followed by the path and filename of the *.pub file that is generated during this process. Copy/paste key. Go to profile setting on GitHub SSH and GPG keys. Click on new SSH key and paste the key in the block. Also give the key a title. The key is also stored /home/technomage/.ssh/id_rsa.pub for future reference.

### How to clone a repository  

All that this mean is that one has a repository on GitHub and one wants to copy the files to one's local computer.  

Copy: SSH address from GitHub repo (clone or download button)  

`git clone <ssh address>`  

*Make sure you are in the directory where the files should be downloaded to when performing this action.*  

To read for instance the `README.md` file:  `cat README.md`  

`git log` Will produce a list of commits with some details and the comments by the person who made the commit.  

### Creating and Setting up a new repository (repo)  

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

### Push requests  

This is effectively getting a file or changes from local machine to GitHub.
Four steps:

1. unstage work
2. stage work
3. commit work
4. push work

After creating a new file or changes it is unstaged.
`~$ git status`
This will list a message:

```bash
  On branch main
  Your branch is up to date with 'origin/main'.

  Untracked files:
  (use "git add <file>..." to include in what will be committed)
        first-push.txt

  nothing added to commit but untracked files present (use "git add" to track)
```

`git add first-push.txt` To stage the new file.       Staging
`git commit -m "First is the first official commit"`  Commit
`git push origin main                                 push  

### Git status command - Modifications - stage, commit, push cyclerm

Modified files

```bash
~$ git status
  On branch main
  Your branch is up to date with 'origin/main'.

  Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
          modified:   first-push.txt

  no changes added to commit (use "git add" and/or "git commit -a")
```

So, the staging, commiting and pushing cycle repeats for the modifications.
If numerous files were modified then `~$ git add .` can be used. (I.e., git add all in current directory)  

### Unstaging and Undeleting files

If file deleted accidentally and the change is staged then use:

```bash
~$ git restore --staged <filename>
```

**Aside:** This actually appears on the git status output so there is no need to remember this command  

To undelete a file when it has not been staged yet.

```bash
~$ git restore <filename>
```

### Git origins and remotes

An origin is where the remote code is being sent to or saved or hosted.

```bash
  ~$ git remote -v
```

Will list all the origins like the following example:

```bash
origin  git@github.com:TechnoMageKOMT/git-essentials.git (fetch)
origin  git@github.com:TechnoMageKOMT/git-essentials.git (push)
```

The origin is simply a distributed place to host code or data. In addition to GitHub, there is also GitLab and BitBucket etc.

- Diminishes risk of losing data.
- Allows for easy sharing of code with collaborators, mentors etc.

### Branching

```bash
git checkout -b new-branch
```

Creates a new branch and switches to the new branch.

```bash
git branch
```

List branches and also an * next to current branch.

```bash
   main
* new-branch
```

```bash
git checkout main
```

Switches back to the main branch.  

The idea is to create "small" and then merging them with the main branch if and when suitable. **NOT** to create extensive very large branches which defeats the purpose of version control.

### Committing to a new branch

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

Log of times, comments and usernames for changes.

### Git fetch

```bash
~$ git fetch origin main
~$ git log --oneline --graph --decorate --all   (Refer alias: glg)
```

The last command will show the latest commit message on GitHub that is not present locally. Using the command glg is a useful way to compare one's local repo with the GitHub repo after using the fetch command. Fetch just downloads the changes but does not apply them.

### File differences

```bash
~$ git diff <filename>
```

This will list the differences applied to a file before staging it. It only works before the file is staged.

### Ignoring files

Create a file called .gitignore and add files to ignore line by line in this file. Wildcards like * can be used to ignore any files with a certain extension etc.

### Correcting bad commit messages

```Git
~$ git commit --amend
```

This will open up nano and the message can be changed, **but** it must take place before the push.

### How to fork a repo

When there is a need to copy entire repos:

1. Download as *.zip
2. Clone (but then still attached to GitHub)
3. Fork into one's own GitHub profile

The forked repo will then effectively be your own to work on as needed. Check on licencing to see how and if the owner is okay with this.

To do this simply click on the "Fork" button and follow the prompts from there.

### Git issues

An issue is a place to talk about something in the code or database. Bring problem to light or make a suggestion or document a bug etc.

### Pull Requests

**Note to self:** Click on "New pull request" button (GitHub interface) and follow the green buttons basically. I'll familiarise myself with this process when I start using Git.

If a branch is deleted during the pull request handling on GitHub, it has to be manually deleted from local Git

```bash
~$ git branch -d <branch name>
```

### Undoing a commit  

To get a quick overview of commit messages:
`~$ git log --oneline`  

Two ways to undo local commits:

- Soft reset
- Hard reset

The hard reset deletes everything up to that commit (recursively).

```bash
~$ git reset --hard 2278f68 (I.e., the hash number of that point)
```

The soft reset retains the file(s) - Better option

```bash
~$ git reset --soft d3a6759
```

### Undo a push (Called a Forced Push)

Not advised and not good practice when working with collaborators. Think twice before ever using this option.

```bash
~$ git reset --hard f79d2a8 (this is the last hash that must be kept. Everything after this will be deleted permanently)
~$ git push origin main (ignore the error messages)
~$ git push origin main --force
```

### How to rebase

Git tree can become very difficult to understand when branching becomes too complex. Rebasing simplify and unite the tree into a single branch but some of the history is lost in the process.

```bash
~$ git rebase <branch name>      (While in main)
```

This is not good practice because there is a loss of traceability or history.

### Merge and Rebase conflicts

Two changes in the same file in the same place.

### How to stash code
