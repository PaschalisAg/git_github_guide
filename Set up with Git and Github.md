Never fear losing work with this professional versioning system

In this tutorial, we walk through the process for using Git locally on your personal computer and using GitHub to back it up. Specifically, we’ll walk through creating your personal GitHub account, setting up Git on your computer, starting your first Git repository, and connecting that repository to a GitHub repository.


## What are Git and GitHub?

This tutorial refers to Git and GitHub repeatedly. _Git_ is a widely-used version control system used to manage code. Git allows you to save drafts of your code so that you can look back at previous versions and potentially undo complicated errors. A project managed with Git is called a _Git repository_.

_GitHub_ is a popular hosting service for Git repositories. GitHub allows you to store your local Git repositories in the cloud. With GitHub, you can backup your personal files, share your code, and collaborate with others.

In short, GitHub is a tool for working with Git. There are other services to host Git repositories, but GitHub is a trusted, free service used by organizations across the world, big and small.

## Create a GitHub Account

To use GitHub, you will need a GitHub account.

In your own browser:

1.  Open a new browser tab
2.  Navigate to [https://github.com/](https://github.com/)
3.  Create an account

If you already have a GitHub account, continue to the next exercise.

After you sign up, you will receive a verification e-mail. Be sure to verify your e-mail address to GitHub by following the instructions in that e-mail.

## Git Setup for Mac and Windows

Next, we will set up Git on your personal computer. Follow the instructions for your operating system.

### Mac users:

1. Launch the **_Terminal_** application. You can find it in **/Applications/Utilities/**. You can also use the **_Spotlight_** search tool (the little magnifying glass in the top right of your screen) to search for **_Terminal_**. Once **_Spotlight_** locates it, click on the result that says **_Terminal_**.  

2. When **_Terminal_** opens, type in `git` and press enter.

3. If you don’t already have Git installed, a dialog will appear saying that “The ‘git’ command requires the command line developer tools. Would you like to install the tools now?” Click “Install”.

![macInstall](https://content.codecademy.com/courses/freelance-1/unit-3/git%20bash%20setup/annotated_xcode_prompt.png)

Then click “Agree to the Terms of Service” when requested.

![macAgree](https://content.codecademy.com/courses/freelance-1/unit-3/git%20bash%20setup/annotated_xcode_terms.png)

4. When the download finishes, the installer will go away on its own signifying that Git is now installed! Click “Done” to finish the installation process.

![macDone](https://content.codecademy.com/courses/freelance-1/unit-3/git%20bash%20setup/annotated_xcode_finished.png)

5. Navigate to GitHub’s articles on setting up your [Git username](https://help.github.com/articles/set-up-git/) and [email](https://help.github.com/articles/setting-your-email-in-git/) and follow the instructions for each using Terminal.

6. GitHub offers two authentication options, HTTPS and SSH, to keep your work secure. This is a security measure that prevents anyone who isn’t authorized from making changes to your GitHub repository. In this article, we will use HTTPS. Navigate to GitHub’s article on [creating a personal access token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) and follow the instructions to configure your computer to be able to use HTTPS.

> Note: As of August 13th, 2021, GitHub uses tokens instead of passwords to authenticate Git operations. More details can be found in [GitHub’s blog post](https://github.blog/changelog/2021-08-12-git-password-authentication-is-shutting-down/).

Now skip down to the “Try it Out!” section below.

### Windows users:

This portion of the guide assumes you have already installed a program called Git Bash which allows us access to Git on Windows. If you have not installed Git Bash, please refer to the previous tutorial on Command Line Interface (CLI) Setup and follow the instructions for installing Git Bash on Windows. Once you complete that you can continue with this guide.

1. Open the Start menu and search for the app, git bash. You should see ‘Git Bash Desktop app’ appear. Press Enter or click on the Git Bash icon to open the app.

![gitBashOpen](https://content.codecademy.com/courses/freelance-1/unit-3/git%20bash%20setup/annotated_gitbash_start.png)

A new window will open that looks like this:

![gitBashShell](https://content.codecademy.com/courses/freelance-1/unit-3/git%20bash%20setup/annotated_gitbash_shell_edited.png)

This window is our CLI, where we will use our Git commands.

2. If you want to make sure that Git is installed, run `git --version` in the CLI. You should see a response that gives you the version of Git installed. It will look like this:

![gitVersion](https://content.codecademy.com/courses/freelance-1/unit-3/git%20bash%20setup/annotated_gitbash_test_edited.png)

Git can now be used in the Git Bash app!

3. Navigate to GitHub’s articles on setting up your [Git username](https://help.github.com/articles/set-up-git/) and [email](https://help.github.com/articles/setting-your-email-in-git/) and follow the instructions for each using Git Bash.

4. GitHub offers two authentication options, HTTPS and SSH, to keep your work secure. This is a security measure that prevents anyone who isn’t authorized from making changes to your GitHub repository. In this article, we will use HTTPS. Navigate to GitHub’s article on [creating a personal access token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) and follow the instructions to configure your computer to be able to use HTTPS.

> Note: As of August 13th, 2021, GitHub uses tokens instead of passwords to authenticate Git operations. More details can be found in [GitHub’s blog post](https://github.blog/changelog/2021-08-12-git-password-authentication-is-shutting-down/).

## Create your first repository

Now you have everything you need to practice your Git skills on your local computer. Take a moment to run the commands below to initialize a Git repository. We will use this Git repository again later in this tutorial so make sure you complete these steps exactly as described.

1.  `mkdir git_practice` to make a new directory to practice.
2.  `cd git_practice` to make the new directory your working directory.
3.  `git init` to turn the current, empty directory into a fresh Git repository.
4.  `echo "Hello Git and GitHub" >> README.txt` to create a new README file (more on this later) with some sample text.
5.  `git add README.txt` to add the new file to the Git staging area.

## Your First Remote Repository on GitHub

Finally, we’ll create a repository on GitHub and then link it to a local repository on your computer. This allows you to backup your work constantly and safely, so you never need to worry about losing your work again!

Now, let’s connect our local Git repository to GitHub.

### Instructions

1. In your Command Line Interface, make sure your current working directory is your new Git repository. Navigate there if not.

2. Check the status of which files and folders are new or have been edited. There should be no files modified.

```
$ git status
```

3. On GitHub, create a new repository by clicking the **New repository** button on the home page.![newRepository](https://content.codecademy.com/courses/freelance-1/unit-3/git%20setup/newrepository.png)

4. On the new repository page, give your repository a name. It’s not necessary, but it would be convenient to name it the same as the directory, **git_practice**. After naming the repository, click **Create repository**.![createRepository](https://content.codecademy.com/courses/freelance-1/unit-3/git%20setup/createrepository.png)

5. After creating a repository, GitHub displays the repository page. At the top of the page, make sure “HTTPS” is selected.![githubHttps](https://content.codecademy.com/courses/freelance-1/unit-3/git%20setup/githubhttps.png)

6.The repository is empty, so it’s time to connect it to your existing work. Copy the Git commands on the GitHub page, under the title “…or push an existing repository from the command line”, and paste them into your Command Line Interface. Running these commands will add a remote repository, and then push your local repository to the remote repository.

When asked for a username and password, type in your GitHub username and password and press `enter` after each. Don’t be alarmed if you can’t see the characters you are typing, they are intentionally hidden as a security measure.![githubCommands](https://content.codecademy.com/courses/freelance-1/unit-3/git%20setup/githubcommands.png)

**Note:** If you set up two-factor authentication with GitHub (don’t worry if you didn’t), follow [GitHub’s instructions on creating a personal access (OAuth) token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) to be used instead of your password in bash. By default, GitHub does not set up two-factor authentication. If you are not familiar with two-factor authentication, you don’t have to generate an OAuth token.

7. Once your Command Line Interface reports that the push is complete, refresh the page on GitHub. You should now see the text you wrote earlier in the README file, “Hello Git and GitHub.”

GitHub automatically displays the contents of a file named **README.txt** if it exists in the repository. The README file is the perfect place to write a description of your project.

