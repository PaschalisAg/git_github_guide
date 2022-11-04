# What is Git?

According to git itself... (run `git help git` to see the same definition)

`Git is a fast, scalable, distributed revision control system with an unusually rich command set that provides both high-level operations and full access to internals.`

If you want to have a look at the documentation, click [here](https://git-scm.com/docs)
# Basic Git Workflow
## git init
With this command we initialize a directory into a Git project.
`init` stand for *initialise*

## Git Workflow explained
A Git project can be thought of having three parts:
1. A *Working Directory*: in this directory we will do all the work.
2. A *Staging Area*: can can think of this part as the place where you list the changes you have made to the working directory.
3. A *Repository*: this is where Git store permanently those changes as different versions of the project.

![](https://content.codecademy.com/courses/learn-git/revised-git-diagram/git%20workflow_fullwidth.svg)
### git status
While working on a project, we make a lot of changes and editing to the files. Git allows us to check the status of these changes with the following command:
`git status`

If we run this command you might see the file where you made some changes to be in `Untracked files`. To clarify that, this does not mean that Git cannot see the file. In contrast, Git does see the file it has just started tracking any changes yet.

```
$ git status

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   scene-1.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        add_tracked_test.rb
        commit_test.rb

no changes added to commit (use "git add" and/or "git commit -a")
```

### git add
In order for Git to start tracking the changes we need to add the file to the *Staging Area*.
To do that we run the following command:
`git add filename
The word filename refers to the file you are ediiting.
To add multiple files to the staging area, you can do it bu running the following command
```
git add filename1 filename2 filename3
```
or
```
git add .
```

After you run this command your file has moved to the area `Changes to be commited`

### git diff
Git allows us to check the differences between the working directory (i.e., the file that we are editing) and the staging area (i.e., the phase that contains all the files that we have staged in order for Git to start tracking the changes) before we commit these changes.
To do that, we run the following command:
`git diff filename`
Once again, "filename" refers to the actual name of the file.
Now after running this command, we will see the phase of the working directory during the *Staging Area* and the phase of the file after the changes. Every change will be marked with a plus (`+`) symbol and it will be in green.
```
$ git diff scene-1.txt

diff --git a/scene-1.txt b/scene-1.txt
index d14d170..081ce08 100644
--- a/scene-1.txt
+++ b/scene-1.txt
@@ -1,2 +1,4 @@
 Harry Programmer and the Sorcerer’s Code: Scene 1
 Dumblediff: I should've known you would be here, Professor McGonagit.
+
+One more line here
```

### git commit 
The *commit* is the last phase in our Git Workflow (see [[#Basic Git Workflow]] and [[#Git Workflow explained]]). With this command we permanently store changes from the **staging area** inside the repository.
The command is as follows:
`git commit -m "message"`
Usually when we commit something, we do it using a commit message. This is indicated by the option `-m` which is followed by a message.

However, there are some Standard Conventions for Commit Messages:
- Must be in quotation marks
- Written in the present tense
- Should be brief (50 characters or less) when using `-m`

In this message, we explain why we did that commit so that other developers know what changes we made.
```
$ git commit -m "add one extra line"

[master (root-commit) 269f076] add one extra line
 4 files changed, 36 insertions(+)
 create mode 100644 add_test.rb
 create mode 100644 init_test.rb
 create mode 100644 scene-1.txt
 create mode 100644 wd_change_test.rb
```

#### git commig amend
Let's assume that you are working on a code and everything seems to work perfectly, so you commit the changes.
However, shortly after you realise that there are some typos in your code, that need to be fixed.
In order to avoid creating a new commit, you can update the previous one using the following command:
```
git commit --amend
```
Git does not exactly uodates the previous commit, it replaces it with the new updated one which is the reason why it asks for a new commit message.

![git-amend](https://static-assets.codecademy.com/Courses/learn-git-github/handy-git-operations/git-commit-amend.png)

However, if we want to keep the same commit message, we can run the following code in our terminal:
```
git commit --amend --no-edit
```

### git log
Git offers another amazing feature. The ability to travel back in time and check older version of a project. This is possible because a commit is stored chronologically in the repository.
We can view older version of a project by running the following command:
```
git log
```

![Git Log output shows recent commit history](https://static-assets.codecademy.com/Courses/learn-git-github/handy-git-operations/git-log.png)

The output logs a list of the commits that you have made.
More specifically, we see:
- A 40-character code, aka *SHA*, that uniquely identifies the commit. In your terminal it will appear in orange text.
- Inside the parenthesis, you will find some information about the branches and the kind of commit you are currenty on (see [[#HEAD commit]] below)
- Next one is the commit author
- The date and the time of the commit
- The commit message

Some other formats of the same command are:
```
git log --oneline
```
Shows the list of commits in one line format.
![Git Log online output shows recent commit history all in one line](https://static-assets.codecademy.com/Courses/learn-git-github/handy-git-operations/git-log-oneline-2.png)

```
git log -S "keyword"
```
Displays a list of commits that contain the keyword in the message.

```
git log --oneline --graph --graph
```
Displays a visual representation of how branches and commits were created. This helps us to make sense of our repository history.
We can use this command without the `--oneline` option, but usually the output is quite lengthy.


## Summary
-   Git is the industry-standard version control system for web developers
-   Use Git commands to help keep track of changes made to a project:
    -   `git init` creates a new Git repository
    -   `git status` inspects the contents of the working directory and staging area
    -   `git add` adds files from the working directory to the staging area
    -   `git diff` shows the difference between the working directory and the staging area
    -   `git commit` permanently stores file changes from the staging area in the repository
    -   `git log` shows a list of all previous commits

Click [here](https://education.github.com/git-cheat-sheet-education.pdf) for a Git Cheat Sheet
![[git-cheat-sheet-education.pdf]]

# Backtracking with Git
Making mistakes or having things that we want to get rid of is something very common when we work on some projects.

### HEAD commit
The `HEAD` commit is the commit that we are currently on or the most recently made commit.
If we want to have a look at the `HEAD` commit, we need to type:
```
git show HEAD
```
The output is something like this:
```
commit b126e74a3b65170a8f1bd124bece7caf27163fe3
Author: codecademy <ccuser@codecademy.com>
Date:   Fri Oct 28 18:42:42 2022 +0000

    initial commit

diff --git a/scene-5.txt b/scene-5.txt
index b12dd97..fa75b29 100644
--- a/scene-5.txt
+++ b/scene-5.txt
@@ -11,4 +11,7 @@ Mark me.
 Hamlet:
 I will.
 
-
+Ghost: 
+My hour is almost come,
+When I to sulphurous and tormenting flames
+Must render up myself.
```
It is similar to the output of the `git log` (see [[#git log]])

### git checkout
To restore the file in our **working directory** to look exactly as it did when we made the last commit, we can use the following command:
```
git checkout HEAD filename
```
another shortcut is as follows:
```
git checkout -- filename
```
Here `filename` is the name of the file that we are working on.

### git reset
In case, before you commit, you have accidentally deleted a very important line of code from your file. Withouth further thinking you `add` the file to the staging area (see [[#Git Workflow explained]]).

To solve this problem you need to run the following command:
```
git reset HEAD filename
```
equivalent to that is the following command:
```
git reset -- filaname
```
This command will basically ***unstage*** that file with the missing but important line of code from the staging area.

However, bear in mind that this command *resets* the file in the staging area to be the same as the `HEAD` commit (see [[#HEAD commit]]). It does not discard file changes from the working directory, it just ==removes them from the staging area==.

```
$ git add scene-2.txt
$ git status

On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   scene-2.txt
        modified:   scene-3.txt
        modified:   scene-7.txt

$ git reset HEAD scene-2.txt

Unstaged changes after reset:
M       scene-2.txt
$ git commit -m "initial commit"

[master 3fc0b0d] initial commit
 2 files changed, 6 insertions(+), 6 deletions(-)
 
$ git status

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   scene-2.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

However, there is another way to reset, this time using an older commit.
By typing:
```
git log
```
You get back the log information with all the commits that you have made so far.
If you want to reset to an older version (i.e., an older commit) you can use the following syntax:
```
git reset first_seven_chars_SHA
```
By using the first 7 character of the SHA (see [[#git log]]) displayed in orange text after you have run the `log` command you can reset to that olde version.
```
$ git log

commit 3fc0b0d3e3a8b5b987d76a39e8774cfd93220523
Author: codecademy <ccuser@codecademy.com>
Date:   Fri Oct 28 19:26:19 2022 +0000

    initial commit

commit d640dc3b22b3ee1d0a6e87477a35fd5e75c0712e
Author: codecademy <ccuser@codecademy.com>
Date:   Thu Nov 5 13:19:17 2015 -0500

    Complete ghost line of dialogue

commit 7be7ec672af73cf31ef72c92e3374fd4e29c675a
Author: danasselin <johndoe@example.com>
Date:   Tue Nov 3 17:15:05 2015 -0500

    Add first page of scene-7.txt

commit 83f7b3591f4ab7aedb3160388b59e65ee1cd94a2
Author: danasselin <johndoe@example.com>
Date:   Tue Nov 3 17:14:48 2015 -0500

$ git reset 3fc0b0d

Unstaged changes after reset:
M       scene-2.txt
```

In order to further understand this travel back in time we can use the following illustration:
![](https://content.codecademy.com/courses/learn-git/git-diagram-3.svg)
Each circle is a commit that we made at a certain point of time, which means that it has each circle has its own SHA.
`HEAD` is the most recent *commit*
When we reset this `HEAD` will move to the commit that we have indicated and the rest of the commits after the point of `HEAD` will be no longer part of our project.

### git stash
We can assume that we are working on experimental code on a fresh branch and at some point we forgot to add something to a previous commit. In order to move to a different branch, one should always be at a clean commit point.
At this point, there is a dilemma since we do not want to commit the experimental code because it is not ready but we also do not want to lose all the code we have been working on.

To save ourselves from this situation, we can "stash" our code in a hidden directory using the command:
```
git stash
```
This command will allow us to get back to a clean commit point with a sychronized working tree and of course since our code is "stashed" will avoid losing any local changes in the process.
In other words, we are "stashing" our local work temporarily in order to update a previous commit and later on retrieve our work.
![In this diagram, a coworker asks the programmer if they can work on something else while they have their current code open. Git stash allows their current code to be stashed as they finish the other update. Git stash pop puts the code changes back into the working directory.](https://static-assets.codecademy.com/Courses/learn-git-github/handy-git-operations/git-stash-pop-diagram.svg)

After running:
```
git stash
```

We can switch branches and do work elsewhere. Once the bug is fixed, or we make the necessary changes to our work, we can "pop" the work that was stored when we used `git stash`, by typing the following command:
```
git stash pop
```
https://www.youtube.com/watch?v=7gL3Safgahk&t=282s&ab_channel=Codecademy

### Git alias commands
When grouping commands together, we might end up having very lengthy lines of Git commands.
Git allows us to create some alias for commands that we run all the time, but following the steps presented below:
```
$ git config --global alias.co "checkout"  
$ git config --global alias.br "branch"  
$ git config --global alias.glop "log --pretty=format:"%h %s" --graph"
```

After running these commands, we can have:
```
git co example
```
Instead of:
```
git checkout example
```