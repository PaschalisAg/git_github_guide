# .gitignore
## What is a .gitignore file and why do we need it?
A `.gitignore` is a plain text file that tells Git to intentionally ignore some changes in certain files. This makes our repository very clean and not messy by containing folders that might be created automatically by the system.
The files that we mostly ignore are:
- configuration files with API or secret keys as`.env`
- compiled binary files or production directories such as `build` or `dist`
- log files
- dependencies downloaded from package managers
- system files as `thumbs.db` on Windows or `.DS_Store` on macOS

### Creating a .gitignore file
There are plenty of ways to create a `.gitignore` file by either using a terminal editor, such as **nano** or **emacs**. We need to make sure that we have the "**.**" included before the name of the file!

Usually we place a `.gitignore` file in the root directory of a repository. We can point out to specific filenames by using relative paths. For instance, let's assume that I want to point out to the `.DS_Store` file inside the my `analysis` folder. To do so, I could add the line:
```powershell
src/analysis
```
Hint: To be able to see all the files in a directory (hidden or not), we need to use a different command:
```powershell
ls -a
```

#### Ignore a directory with `.gitignore`
If we want to ignore entire directories, we can do so by adding a forward slash after the name of the directory. For instance,
```powershell
node_modules/
```

#### `.gitignore` Patterns
We can take advantage of [patterns](https://git-scm.com/docs/gitignore#_pattern_format) to match multiple filenames. These help us handle special cases such as ignoring specific file types or ignoring all but one file inside a directory. Some examples of things that make up patterns are:

-   Wildcard `*` to match 0 or more characters except for `/`. For example, adding `*.html` to **.gitignore** would ignore all files ending with the `.html` extension. `example*` would match any file starting with `example` such as `example.txt` or `exampleHtmlFile.html`.
-   Negation `!` as a prefix to negate any file that would otherwise be ignored. For example,
    
    ```powershell
    index*!public/index.css
    ```
    
    will ignore all files starting with `index` except for `src/index.css`. But, we cannot negate a file inside an ignored directory.
-   Square brackets `[]` can be used to match a single character from a set of characters or a range of characters. Note that the range can be alphabetical: `[a-z]` or `[A-Z]`, numeric `[0-9]`, or a set of characters. If we added `index.[a-i]*` with both the square bracket and wildcard to **.gitignore**, we would ignore `index.css` and `index.html` but not `index.js`, since “j” is outside of the `[a-i]` range.
-   Double asterisk `**` is used to match 0 or more directories. If we had a **temp** folder inside all of the folders in the root directory and we only wanted to match files with the `.log` extension, we could use the pattern `**/temp/*.log`.

## GitHub Provided Templates

When we create a new repository on GitHub, we have the option to add a **.gitignore** file from a list of templates. These templates are pulled from [GitHub’s gitignore repository](https://github.com/github/gitignore). For example, below is the template for Java projects.

```
# Compiled class file
*.class 

# Log file
*.log

# BlueJ files
*.ctxt 

# Mobile Tools for Java (J2ME)
.mtj.tmp/ 

# Package Files #
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar
```