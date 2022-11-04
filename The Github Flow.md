# Introduction 
The Github flow is essential for every project. With that said, following a specific workflow allows the project to move in a more orderly way. By sticking to a workflow, team members will be able to isolate their work and avoid any conflicting code from being merged.

The basic workflow used with GitHub is as follows:
1. Create a branch
2. Commit changes
3. Create a pull request
4. Review pull request
5. Merge and delete branch

# The Github flow explained
## Creating and managing branches
A branch is essentially a divergence from the main project or if we can put it that way, a different path other than the main path of a road.
When we branch out, git makes a new state of the current code, upon which we can work and make as many changes as we want without affecting the important main state of the code.
With that said, a GitHub repository can have one or more branches.
However, it is very important to remember at this point that there is also the `main` branch. This is the branch where we work by default, unless we create a new branch and we move there to work on the code. SInce `main` is where we work by default is good to keep this branch as clean as possible and only include cleaned and production code.
When you are working on a branch and you have something that works and your work is reviewed by your supervisors, you can merge the work into the project (i.e., the `main` branch).

By working using branches git allows us to work on our code withouth creating conflicting versions of other's code or even messing up the whole project. In other words, it is a way to ensure that the project will work without any problems.

Some conventions about the name of the branch is that it needs to have a descriptive name. A good branch name is the following:
`doe_update_dashboard_notifications`
It has the author's name
The branch type
And a short branch description

![branch flow](https://static-assets.codecademy.com/Courses/learn-git-github/github-flow/github-flow-branch.svg)

## Adding and Commiting changes

Let's assume that you were recently assigned to a team to develop a new method to approach texts.
The first you need to to do is to clone (i.e., download) the repository and then create a branch for your feature of the `main` branch (see [[#Creating and managing branches]]), and begin coding a new file in your local Git environment.
After testing your code and ensuring that everything is running correctly, you need to push those changes with a commit.

As a refresher, the `git commit`[[^]] command records change to one or more files in your branch, assigning the commit a unique ID that identifies who created the changes, what changes were created, and when the changes were created.

You can commit along with a message describing your work, and lastly, push the commit (see [[Git#git commit]]) to the remote Github repository.
![commit changes](https://static-assets.codecademy.com/Courses/learn-git-github/github-flow/github-flow-commit-changes.svg)
## Pull requests
Before merging the changes to the `main` branch our code should be reviewed.
Pull requests on GitHub allow collaborators to review and give feedback on proposed code changes before they are merged to the main branch.
After the changes have been approved you can merge them into the `main` branch.

When creating pull requests, it is imperative that you include as much relevant detail in the description as possible in order to save review time and of course to ensure that the code runs properly.
![open pull request](https://static-assets.codecademy.com/Courses/learn-git-github/github-flow/github-flow-open-pull-request.svg)
## Reviewing and Merging a Pull Request
Once you’ve created a pull request, other members in your team can review it up on GitHub.

The pull request should include a description and GitHub will display all the files with the changes created. Each line of code will have a clickable “+” button where you can add a comment in regards to the line.

While reviewing, it’s important to be constructive with feedback and be precise about what needs to be changed. Here are few best practices when reviewing code:

-   Don’t only comment on _what_ should be changed, but _why_ it should be changed. Feel free to provide resources to make your point.
    
-   Be as clear as possible with your comments and make sure to be clear as to what to modify.
    
-   Look at the bigger picture and try to spot potential errors. Would the submitted code produce any obstacles if the project scales?
    

Once all the feedback is added, collaborators can click on “Submit Review” and wait for a response. If all goes well, the pull request will eventually be merged into `main`!
![review pull request](https://static-assets.codecademy.com/Courses/learn-git-github/github-flow/github-flow-review-pull-request.svg)
## Deleting a Branch and Review
Once changes are merged, in order to keep things organized and managed, it’s imperative to only keep active branches and delete the closed ones.

With that in place, this wraps up the flow of working on a project using Github. We explored:

-   The importance of creating branches and isolating work from the `main` branch.
    
-   Best practices of naming branches and making commits on branches.
    
-   What a pull request is: a discussion page for a set of code changes between one branch and another.
    
-   Merging a branch and delete it once it’s merged.
    

This covers the main steps of working with a team and managing the workflow using Github.

Github provides us with a number of useful tools that expand on Git functionality, especially if we’re collaborating with teammates!
![merge delete branch](https://static-assets.codecademy.com/Courses/learn-git-github/github-flow/github-flow-merge-delete-branch.svg)