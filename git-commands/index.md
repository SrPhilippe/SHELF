# Git commands

| Navigation                 |
| -------------------------- |
| [🠜 go back](../readme.md) |

- `git init`: Initiates a git repository

- `git add filename.ext`: Stages the `filename.ext` for commit
  - If you use a dot <kbd>.</kbd> instead of the file name, all the changes will be staged

- `git status`: Show the current branch status

- `git commit -m "commit message"`: make a commit with a custom message for all the staged files

- `git push`: Pushes all the commits to the [HEAD](#head) branch

- `git branch`: Creates a new branch

  - > Tip: When creating a branch _e.g._ `git branch development`, you can publish this branch with the following command: `git push --set-upstream origin development`

- `git marge`: Unifies two or more histories together
  - > The [HEAD](#head) should be pointing to the ramification who will receive the merged files. So if you want to merge the development branch into the main, you should do `git checkout main` and then `git merge development`

- `git remote`: List of the [remote](#remote) connections you have to other repositories
  - `git remote -v`: Same as the above command, but include the URL of each connection
  - `git remote add <name> <url>`: Create a new connection to a remote repository
  - `git remote rm <name>`: Remove the connection to the remote repository called ＜name＞

---

<details>
<summary>I don't know what to do with these guys for know</summary>
`git remote -v`<br>
`git remote add`<br>
`git remote remove`
</details>

## Understanding the names

<details id="head">
<summary>What is <b>HEAD</b></summary>
You can think of the arrow in a git graph. The arrow will point to the current selected branch, thus HEAD means where we are in the project at the moment.
</details>

<details id="origin">
<summary>What is <b>origin</b></summary>
Origin is an alias for the remote repository that the project was originally cloned from.
</details>

<details id="remote">
<summary>What is <b>Remote</b></summary>
The git remote command lets you create, view, and delete connections to other repositories. Remote connections are more like bookmarks rather than direct links into other repositories. Instead of providing real-time access to another repository, they serve as convenient names that can be used to reference a not-so-convenient URL.
See more <a href="https://www.atlassian.com/git/tutorials/syncing" rel="noopener" target="_blank">in Bitbucket</a>.
</details>

<details id="upstream">
<summary>What is <b>upstream</b></summary>
Upstream refers to the original repo or a branch. For example, when you clone from Github, the remote Github repo is upstream for the cloned local copy.
</details>

## How to tell git who you are?

After installing git in our computer and before we can make any commits, we must tell git who we are passing some global or local informations.

- `git config --global user.email <email>` this command sets a global user email

- `git config --global user.name <username>` this command sets a global user name

After this, if you try to publish a repository with vscode, an authentication window will pop in order to check the credentials to start the push.

## How to set the default editor to open with git

```git
git --global editor.core <editor-here> -w
```

- _E.g._ Setting vscode as the default editor

```git
git --global editor.core "code" -w
```

| Navigation                 |
| -------------------------- |
| [🠝 go top](#git-commands) |
| [🠜 go back](../readme.md) |
