## git branch
Git allows us to create branches to experiment and work on different versions of a project.

To see on which branch you are on, you simply have to type:
```
git branch
```
The asterisk has all the information for you.

## branching overview

![The diagram shows a new branch being formed off the main branch.](https://content.codecademy.com/courses/learn-git/git-diagram-1.svg)
- The circles are the commits; all together they form the Git project's commit history.
- *New Branch* is a different version of the Git project

## create a new branch
By default, Git has only one branch, `master`.
To create a new branch, use the following command:
```
git branch new_branch_name
```
- `new_branch_name`: will be the name of the new branch. This name should be descriptive and it cannot contain any whitespaces (e.g. `new_branch` and `new-branch` are valid names, but `new branch` is not).
Keep in mind that by creating a new branch you are not automatically moving to it.

## moving to a new branch
To move to a new branch, you need to use the already known `git checkout` command (see [[Git#git checkout]]) 

So if you type:
```
git checkout new_branch_name
```
If you run `git branch`, you will the asterisk on the new branch name.

From now on, all the commits that you can do on the `main` branch, you can do them on your new branch.

## git merge
If you are done with your changes and you want to include your branch to the `main` branch, you need to run the following command:
```
git merge new_branch_name
```
Keep in mind that your goal is to update `master` with the changes you made on the new branch and **NOT** vice versa.
Thus, the giver branch is the new branch and the receiver branch is the `main` branch.

If the latest commit in in the new branch, then Git will "fast-forward" `master` to be up to date with fencing.

### merge conflict
We will have a conflict with the merging of the new branch to the `main` if we update the latter prior to the former.
This happens because Git does not know which changes you want to keep. This is called a ***merge conflict***.

## delete branch
When we are done and we don't need the new branch anymore, we can delete it. The goal end is to integrate all the changes into the `main` branch. Once this has been done then the branch has served its purpose and can be deleted.
The command to do that is the following:
```
git branch -d new_branch_name
```
If the branches have never been merged to the `main` branch, we will need to write a different command:
```
git branch -D new_branch_name
```

## Summary
Git _branching_ allows users to experiment with different versions of a project by checking out separate _branches_ to work on.

The following commands are useful in the Git branch workflow.

-   `git branch`: Lists all a Git project’s branches.
-   `git branch branch_name`: Creates a new branch.
-   `git checkout branch_name`: Used to switch from one branch to another.
-   `git merge branch_name`: Used to join file changes from one branch to another.
-   `git branch -d branch_name`: Deletes the branch specified.