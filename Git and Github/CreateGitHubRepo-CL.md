
## First using gh
[How-To-Geek: How to Create and Manage a Github Repository From the Command Line](https://www.howtogeek.com/devops/how-to-create-and-manage-a-github-repository-from-the-command-line/)
Log in to GitHub::  ==gh auth login==
::This will prompt you for a few things, and finally ask you to log in with your browser through Oath, or manually create and paste an authentication token from your account's security settings.

 Create new-repo::  ==gh repo create new-repo --private==

The Github CLI has a bunch of other subcommands for working with repos:

-   `gh repo edit`, which [can set a lot of different config flags](https://cli.github.com/manual/gh_repo_edit), such as the default branch, whether the issues/wiki/project pages are turned on, and your homepage and description.
-   [gh repo fork](https://cli.github.com/manual/gh_repo_fork), which works like `git clone` except forking the target repository and making a copy in your account.
-   [`gh repo list`](https://cli.github.com/manual/gh_repo_list), which prints out a list of your repositories.
-   [gh repo rename](https://cli.github.com/manual/gh_repo_rename), changes the name and URL.

## Then using Git
```
echo "# new-repo-name" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/Your-github-username/new-repo-name.git
git push -u origin main
```




### [ hub is a project  on GitHub that automates CL GitHub actions](https://hub.github.com/)
[hub installation options](https://github.com/mislav/hub#installation)
1) Create a new git repo::  git init new-repo-name
2) Switch to new-repo directory::  cd new-repo
3) Create a new GitHub repo::  hub create -p new-repo-name![[Pasted image 20230912081057.png]]