# Git commands

[🠜 go back](../readme.md)

- `git init`: Initiates a git repository

- `git add filename.ext`: Stages the `filename.ext` for commit
  - If you use a dot <kbd>.</kbd> instead of the file name, all the changes will be staged

- `git status`: Show the current branch status

- `git commit -m "commit message"`: make a commit with a custom message for all the staged files

- `git push`: Pushes all the commits to the HEAD branch

- `git branch`: Creates a new branch

  - > Tip: When creating a branch _e.g._ `git branch development`, you can publish this branch with the following command: `git push --set-upstream origin development`



<details>
<summary>I don't know what to do with these guys for know</summary>
`git remote -v`<br>
`git remote add`<br>
`git remote remove`
</details>

## Understanding the names

<details>
<summary>What is <b>origin</b></summary>
Origin is an alias for the remote repository that the project was originally cloned from.
</details>

<details>
<summary>What is <b>upstream</b></summary>
Upstream refers to the original repo or a branch. For example, when you clone from Github, the remote Github repo is upstream for the cloned local copy.
</details>

## How to tell git who you are?

After installing git in our computer and before we can make any commits, we must tell git who we are passing some global or local informations.

- `git config --global user.email` this command sets a global user email

- `git config --global user.name` this command sets a global user name

After this, if you try to publish a repository with vscode, an authentication window will pop in order to check the credentials to start the push.

## How to set the default editor to open with git

```git
git --global editor.core <editor-here> -w
```

- _E.g._ Setting vscode as the default editor

```git
git --global editor.core "code" -w
```

[🠝 go top](#git-commands)<br>
[🠜 go back](../readme.md)
