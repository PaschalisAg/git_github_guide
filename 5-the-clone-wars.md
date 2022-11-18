# The Clone Wars
## 1 git clone
Part of Git is also **teamwork**.
In any time, Git allows to store a remote repository (i.e., a repository uploaded on Github) locally in our computer.
To do so, we need to run the following command:
```
git clone remote_location clone_name
```
- `remote_location`: is where Git can find the remote repository. Usually it is a web address, but it can also be a filepath.
- `clone_name`: it is the name we give to the directory in which Git will clone the repository. In other words, the name of our clone. The `clone_name` will be our local copy of the remote repository from Github.

## 2 git remote -v
When we clone a remote repository, Git does something behind the scenes.
What it does is to give the remote address the name *origin*, so that we can refer to the remote repository more conveniently.

We can see a list of a Git project's remotes with the command:
```
git remote -v
```

After running this command, Git will list the name of the remote (i.e., `origin`), as well as its location
The remote is listed twice: once as `fetch` and once as `push`.

## 3 git fetch
Let's assume that you clone a repository, but in the meantime the moderator made some changes.
A very easy and handy way to see if changes have been made to the remote repository and at the same time bring the changes back to your local copy is with the following command:
```
git fetch
```
Keep in mind, that this command will not ***merge*** changes from the remote into your local repository. It will bring these changes onto what's called a *remote branch*. In other words, this command will only track if there are any changes in the remote repository.
Thus the output will look something like this:
```
remote: Counting objects: 5, done.
remote: Compressing objects:  20remote: Compressing objects:  40remote: Compressing objects:  60remote: Compressing objects:  80remote: Compressing objects: 100remote: Compressing objects: 100% (5/5), done.
remote: Total 5 (delta 1), reused 0 (delta 0)
Unpacking objects: 100% (5/5), done.
From /home/ccuser/workspace/curriculum-a/science-quizzes
 * [new branch]      master     -> origin/master
```
## 4 git merge
We have already covered what `git merge` (see, [[Git and branches#git merge]]) actually does, but now let's see what it does when it comes to a remote repository and its fetched version.

The output above shows the new commits that the moderator did to the project have been fetched to our local copy of the Git project, and that those commits are on the `origin/master` branch.
However, the *local* `master` branch has not been updated yet, so we can't view or make changes to any of the work she has added.

The only step left to see the repository with the newly updated commits is to *merge* the two branches (i.e., the `origin/master` branch with our `main` local branch) (tip: remember that `origin` is the alias of the remote repository (i.e., the repository that is uploaded on Github)).
With that said, by running the following command we have this accomplished:
```
git merge origin/master
```

## 5 git push
If we want to push the changes up to the remote, `origin`, we run the following command:
```
git push origin our_branch_name
```
This way Sally will be able to review our branch and, if necessary to `merge` our work into the `master` branch.

## 6 Git workflow for collaborations

Now that we've merged `origin/master` into your local `master` branch, you’re ready to contribute some work of your own. The workflow for Git collaborations typically follows this order:

1.  Fetch and merge changes from the remote
2.  Create a branch to work on a new project feature
3.  Develop the feature on your branch and commit your work
4.  Fetch and merge from the remote again (in case new commits were made while you were working)
5.  _Push_ your branch up to the remote for review

Steps 1 and 4 are a safeguard against _merge conflicts_, which occur when two branches contain file changes that cannot be merged with the `git merge` command.

## 7 Summary
-   A _remote_ is a Git repository that lives _outside_ your Git project folder. Remotes can live on the web, on a shared network or even in a separate folder on your local computer.
-   The _Git Collaborative Workflow_ are steps that enable smooth project development when multiple collaborators are working on the same Git project.

We also learned the following commands

-   `git clone`: Creates a local copy of a remote.
-   `git remote -v`: Lists a Git project’s remotes.
-   `git fetch`: Fetches work from the remote into the local copy.
-   `git merge origin/master`: Merges `origin/master` into your local branch.
-   `git push origin <branch_name>`: Pushes a local branch to the `origin` remote.
