
# git-intro

By Jonathan Neidel @jneidel

Online at: jneidel.com/git

---

# What we will cover

- What is git?
- Creating a github repo
- Editing files with git
- Publish a website via github pages
- Collaborative workflow

---

# Prerequisites

- git
- GitHub account

---

# What is git?

A version control system for tracking changes in files and coordinating work on those files with multiple people.

Concretely this means:

- History of all changes
- Multiple versions of the same file
- Central storage for your files (github)
- Collaborative workflow

---

# Starter files

**Get files:**

- Download starter files jneidel.com/git-starter.zip
- Unzip using WinRar, 7zip, etc.
- Move unpacked folder to desktop

**Open terminal:**

- Mac/Linux: Search applications for 'terminal'
- Windows:   Search applications for 'cmd'

**Open starter files in terminal:**

```zsh
$ cd ~/Desktop/git-starter (cd...change directory)

$ ls  # unix (ls..list directory contents)
$ dir # windows

You should see:
index.html
style.css
```

---

# Create github repo

- Click the plus in the navigation bar -> 'New repository' or go to github.com/new
- Set name, click 'Create repository'
- Click green 'Clone or download' button to the right
- Copy the given url (for example: https://github.com/jneidel/test.git)

---

# git init

After creating the repo on github also create a local git repo.

```zsh
$ git init
```

---

# git remote

Add github repo to local one

```zsh
$ git remote add origin <your-repo-link>
```

`origin` is the conventional name for your upstream repo.

---

# git status

See if files have been changed, whenever they are staged

```zsh
$ git status
```

---

# git add

Stage files for commit

```zsh
$ git add *
```

Takes any fuzzy search:

```zsh
$ git add index.html
$ git add *.html
$ git add index.*
```

Or multiple:

```zsh
$ git add index.html style.css
```

---

# git commit

Apply changes

```zsh
$ git commit -m "Initial commit"
```

## Commit message

Commits should be atomic, only include a distinct change:

Good:

- "Change background color"
- "Update options section in readme"
- "Add webpack config"

Bad:

- "Add changes" - Too unspecific
- "Change color, add header, refactor tests" - Too much content, split up in different commits

Commits should be sound like this: If applied this commit will <commit-message>.

For example: If applied this commit will "Change [the] background color".

Commits should be capitalized followed be only lower case words (function names, etc. are exceptions)

---

# git push

Synchronize local version of the repo with github.

```zsh
$ git push origin master
```

Or in words: `push` current changes to the branch `master` of the remote repository `origin`.

---

# GitHub Pages

- Open your github repository
- Click on the settins tab
- Scroll down to 'GitHub Pages'
- In the dropdown: choose 'master branch' as source, click 'Save'
- Scroll down again
- Open the link that is now available (eg: https://jneidel.github.io/test/)

This is where your project will be published.

Once github pages has built the site, append an `/index.html` to the url. (eg: https://jneidel.github.io/test/index.html)

---

# Feature branches

If working with multiple people you don't want everybody to commit to master. This would lead to a lot of different versions of the same files, which would be hard to merge back together. To avoid this one will create a feature branch before starting to work.

```zsh
$ git checkout -b change-color
```

Make changes to files and push to github.

---

# git branch

To see current branch:

```zsh
$ git branch
```

To delete the feature branch, first go back to the master branch:

```zsh
$ git checkout master
$ git branch -d change-color
```

---

# Github pull request

To merge your changes on the feature branch back into `master` open a pull request on github.

- Open repo on github
- Click on branches tab
- Click on 'New pull request' button next to feature branch
- Make sure `master` is the base branch
- Describe changes
- 'Create pull request'

Before merging a pull request, let somebody from your team do a code review. In your code review you step through the changes together to catch any flaws.

---

# Merge conflicts

