## Git Rebase
### When do we use this command?
When working with a Git repository, we might need at some point to combine changes from the working branch into another one (**NOT** into the `main` branch).
We can do that, by using `git merge` or `git rebase`.

### What is Git Rebase?
On a very abstact level, `git rebase` works as moving the base of a branch to a different position. 

![A diagram showing that before rebase, branch commits stick out from the main line of development.](https://static-assets.codecademy.com/Courses/learn-git-github/git-rebase/before-rebase.svg)

![A diagram showing that after rebase, commits over multiple branches get flattened into a single line.](https://static-assets.codecademy.com/Courses/learn-git-github/git-rebase/after-rebase.svg)
By "rebasing" we can keep the Git commit history clean and easy to follow since the `new_feature` is rebased onto the `main` one, and we move all the changes made from `new_feature` to the front of `main` and incorporate the new commits by rewritting its history.

#### Major benefits of `git rebase`
- Eliminates unecessary merge commits required by `git merge`.
- The history of the changes made in the `main` branch remains linear and follows a clear path of changes.
- We can navigate the changes easier when viewing the changes in a `log` or `graph`.

### Merge vs Rebase

`git merge`: joins two or more development histories together by creating a new merge commit.
`git rebase`: reapplies commits on top of another base branch.

`git merge`: preserves history as it happened, whereas rebase rewrites it.
`git rebase`: rebase rewrites the history.

`git merge`: useful to use when the commit graph is relatively easy to read
`git rebase`: useful to use when the commit history becomes really difficult to read.

`git merge`: since it joins the histories of two developmental branches, the history is preserved with its branches.
`git rebase`: the commit history is displayed as linear.

![In the diagram, the history from only using Git merge shows lots of different paths representing different branches. Next to it, the path from using Git rebase is one straight line, with commits from a feature branch getting represented as a commit on the main branch.](https://static-assets.codecademy.com/Courses/learn-git-github/git-rebase/git-merge-vs-git-rebase.svg)

`git merge`: we use it when we want to add changes of a branch back into the `main branch`.
`git rebase`: we use it when we want to add changes of a `base` branch back to a branched out branch.

### Disadvantages
`git rebase` it is a destructive operation since it creates new commits, which can make it complicated to track the context of any changes made, thus it is better to use `rebase` locally. In other words, once something has been pushed, **DO NOT** rebase it.
Since we’re rewriting history we will also have to solve more commit conflicts. When we merge a branch, we only need to solve the conflicts once straight into the merge commit. However, when using rebase we might end up having to solve similar conflicts in previous commits that are being rewritten because rebase practically cherry-picks each commit individually and attempts to merge it in. If a commit introduces a conflict, rebase will complain about it even if the conflict is fixed in subsequent commits. In order to reduce the number of merge conflicts, it’s suggested to rebase often and to also squash changes into one commit as much as possible.
Moreover, make sure that the branch we’re working on is not a shared branch. A shared branch meaning a branch that exists on the distant repository and that other people on our team could pull. Why should we avoid this? Well, remember that rebasing changes **commit history**. So if we share our commits publicly, and others start additional work based on those commits, our trees are no longer in sync after rebasing. As a golden rule, it’s important to only use rebase on a local branch that we’re working on individually.