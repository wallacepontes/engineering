# git-cheatsheet

Git commands:

1. **git merge**: This command is used to integrate changes from one branch into another. 

> For example, if you have a feature branch and you want to incorporate those changes into the main branch, you would use `git merge`. This is often done as part of a pull request on online Git platforms like GitHub or GitLab.

2. **git fetch**: This command fetches changes from a remote repository but does not merge them into your local branch. 

> It's useful to see what changes others have made online without affecting your local branch.

3. **git reset**: This command is used to reset your current branch to a specific commit. 

> In an online context, it might be used to undo a commit before pushing it to a remote repository or to unstage changes before committing them.

4. **git add**: This command stages changes for the next commit. In an online context, you would use `git add` to prepare the changes you want to include in your next commit before pushing them to the remote repository.

> * To add a single file: `git add <file>`
> * To add everything at once: `git add -A`

> **Important**: The `git add` command doesn't change the repository and the changes are not saved until we use `git commit`

5. **git commit**: After using `git add` to stage changes, you use `git commit` to record those changes as a new commit in your local repository. Once committed, you can push these changes to the remote repository.

> * `git commit -m "commit message"`

> **Important**: `git commit` saves your changes only **locally**.

6. **git push**: This command uploads your local commits to a remote repository, making them available for others to see and work with online. For example, after committing changes locally, you would use `git push` to share those changes with your team.

> * `git push <remote> <branch-name>` : Git push uploads your commits to the remote repository 

> After you created your branch locally as 
> * `git checkout -b your_branch` 

> Then you can work locally in your branch, when you are ready to share the branch, push it.
> * `git push -u origin your_branch` or 
> * `git push --set-upstream <remote> <name-of-your-branch>`

> Your Teammates/colleagues can push to your branch by doing commits and then push explicitly
> * `git push origin HEAD:refs/heads/your_branch`

> * git -c http.sslVerify=false push

> **Important**: Git push only uploads changes that are committed.

> Go back to the selected commit on your local environment
> * `git log --oneline`
> * `git checkout <commit-id> .` 

7. **git pull**: `git pull` fetches changes from a remote repository and merges them into your current branch. This is a common command to ensure your local branch is up to date with the online repository.

> * git pull origin BRANCH_NAME
> * git -c http.sslVerify=false pull

> **Important**: How to resolve git pull, fatal: unable to access. Empty reply from server

> Go to Windows Credentials and update the password


8. **git clone**: `git clone` is used to create a copy of a remote repository on your local machine. It's often the first step when you want to work on an existing online project locally.

> * `git clone <https://name-of-the-repository-link>`

> Note: use the depth parameter to reduce the clone size and speed up the clone.
> * `git clone --depth=1 <https://name-of-the-repository-link>`: These clones truncate the commit history to reduce the clone size.

> How do I set GIT_SSL_NO_VERIFY for specific repos only?

[How do I set GIT_SSL_NO_VERIFY for specific repos only?](https://stackoverflow.com/questions/9008309/how-do-i-set-git-ssl-no-verify-for-specific-repos-only)

> * `git -c http.sslVerify=false clone <path>`

9. **git checkout**: This command is is a useful and multi-purpose command. You can use it to create new branches, checkout a branch, checkout specific commits, and more.

> How do you change to a new branch after you cloned from a branch?
> * `git branch mynewlocalbranch`
> * `git checkout mynewlocalbranch`

> How to switch to an existing branch
> * `git checkout master` : Switched to branch 'master'

> This command will create a branch **locally**:
> * `git checkout -b mynewlocalbranch` 

> There is also a handy shortcut for returning to the previous branch you were on by passing `-`
> * `git checkout -` 

> To checkout a specific commit, you just need to pass the commit's SHA as the parameter
> * `git checkout SHA` 

>  There are some steps you need to follow for successfully switching between branches:
> * The changes in your current branch must be committed or stashed before you switch
> * The branch you want to check out should exist in your local

> For **Tracking Branches**, the simple case is the example you just saw, running 
> * `git checkout -b <branch> <remote>/<branch>`

10. **git stash**: `git stash` is used to temporarily save changes that you don't want to commit but also don't want to lose. In an online context, you might stash changes when you need to switch to a different branch or pull in changes from a remote repository.

> * `git stash apply` : After stashing changes, you can use `git stash apply` to reapply the changes to your current branch. This is useful when you want to bring back the stashed changes to continue working on them.

> * `git stash pop` : Similar to `git stash apply`, `git stash pop` reapplies the stashed changes to your current branch. However, it also removes the stash entry, so it's often used when you're confident that you won't need to apply the same stash again.

11. **git branch**: Branches are highly important in the git world. By using branches, several developers are able to work in parallel on the same project simultaneously. We can use the git branch command for creating, listing and deleting branches.

* Creating a new branch: `git branch <branch-name>` . This command will create a branch **locally**.
* List all branches (local/remote): `git branch -a`
* Viewing branches: `git branch` or `git branch --list`
* Deleting a branch: `git branch -d <branch-name>`
* To push the new branch into the remote repository: `git push -u <remote> <branch-name>`
* if you want to see what tracking branches you have set up, you can use: `git branch -vv` or `git branch -avv`
* The command to delete a local git branch can take one of the following two forms: `git branch --delete old-branch.` or `git branch -d old-branch.`

12. **git status**: This command gives us all the necessary information about the current branch.  

> Maybe you will see that there are file names that are red - this means that they're unstaged files. The unstaged files won't be included in your commits.

> To include them, we need to use `git add`

> With `git status` we can gather information like:
> * Whether the current branch is up to date
> * Whether there is anything to commit, push or pull
> * Whether there are files staged, unstaged or untracked
> * Whether there are files created, modified or deleted

13. **git log**: This command is used to list all commits made. 

> How to find a commit SHA: One way to find the SHA of a commit is to view the `git log`. A SHA is a unique identifier that is generated for each commit.

> * `git log --oneline` : list all commits in one line

14. **git switch**: This command is used to undo any changes you make and return to your previous branch.

> * `git switch -` : undo any changes you make and return to your previous branch.
> *  `git switch -c <new-branch-name>` : If you instead want to keep your changes and continue from here, you can use it to create a new branch from this point.

> What is a detached HEAD state? From this position you have two options:
> * Experiment and then throw away your changes by returning to your previous branch
> * Work from here and start a new branch from this point

15. **git submodule add URL**: Absolute or relative URL of the project you would like to start tracking

> * `git submodule add` : How to add a submodule to your project
> *  `git submodule update` : How to clone a project that has submodules, and how to update the submodules.

> How to manage submodules:
> * `git submodule status` :
> * `git submodule foreach` :
> * `git submodule sync` :
> * `git submodule deinit` :
> * `git submodule summary` : command to see the changes made in the submodules

> Tips and best practices for using submodules, such as:
>  - Use submodules only for projects that you don’t need to modify, or that you can contribute to upstream.
> - Keep the submodules as small and focused as possible, and avoid adding unnecessary dependencies.
> - Update the submodules regularly, and make sure they are in sync with the main project.
> - Document the purpose and usage of the submodules in your project’s README file.


16. **git tag**: This command lists the tags in alphabetical order; the order in which they are displayed has no real importance. Allows you to mark specific points in a repository’s history as being important. 

> * `git tag` : with optional -l or --list options, you can list the existing tags in Git 

> Git supports two types of tags: lightweight and annotated. A lightweight tag is just a pointer to a specific commit, while an annotated tag is a full object that contains the tagger name, email, date, message, and can be signed and verified with GPG.

> * `git tag -a <tagname> -m <message>`: To create an annotated tag
> * `git show <tagname>`: You can see the tag data along with the commit that was tagged
> * `git tag -d <tagname>`: You can delete a tag 
> * `git push <remote> <tagname>`: You can push tags to a remote server 
> * `git push --tags`: to push all tags at once

> You can check out tags like branches by using the command `git checkout <tagname>`, but this puts you in a detached HEAD state, which means you cannot make any commits.
> * `git checkout -b <branchname> <tagname>`: To work on a version of your project at a specific tag, you can create a new branch from the tag

> * `git tag -a <tagname> <commit>`: You can create tags later for past commits and specifying the commit checksum or part of it.

> * `git tag -s <tagname> -m <message>`: You can also create signed tags
> * `git tag -v <tagname>`: verify tags

17. **git rebase master**: you can take all the changes that were committed on one branch and replay them on a different branch.

> * `git checkout experiment`
> * `git rebase master`

> At this point, you can go back to the master branch and do a fast-forward merge.
> * `git checkout master`
> * `git merge experiment`

> rebasing makes for a cleaner history. If you examine the log of a rebased branch, it looks like a linear history: it appears that all the work happened in series, even when it originally happened in parallel.

> **Rebase vs. Merge**
> - Now that you’ve seen rebasing and merging in action, you may be wondering which one is better. Before we can answer this, let’s step back a bit and talk about what history means.

18. **git diff**: Show changes between commits, commit and working tree, etc

19. **git ls-files**: To show files currently tracked by git 

## Tracking branches

The ProGit book has a very good explanation, see reference *Tracking Branches - ProGit book* and *What is a tracking branch?* 

Checking out a local branch from a remote branch automatically creates what is called a tracking branch. Tracking branches are local branches that have a direct relationship to a remote branch. If you’re on a tracking branch and type git push, Git automatically knows which server and branch to push to. Also, running git pull while on one of these branches fetches all the remote references and then automatically merges in the corresponding remote branch.

When you clone a repository, it generally automatically creates a master branch that tracks origin/master. That’s why git push and git pull work out of the box with no other arguments. However, you can set up other tracking branches if you wish — ones that don’t track branches on origin and don’t track the master branch. The simple case is the example you just saw, running git checkout -b [branch] [remotename]/[branch]. 

* If you have Git version 1.6.2 or later, you can also use the --track shorthand: `git checkout --track origin/serverfix`

* To set up a local branch with a different name than the remote branch, you can easily use the first version with a different local branch name: `git checkout -b sf origin/serverfix`

## Git Bitbucket

1. fatal: unable to access 'https://bitbucket.org/entel_fuentes/repo_portgateway_21.git/': Failure when receiving data from the peer

[RPC failed; curl 56 Failure when receiving data from the peer](https://community.atlassian.com/t5/Bitbucket-questions/RPC-failed-curl-56-Failure-when-receiving-data-from-the-peer/qaq-p/2239271)

* git config --global http.sslBackend openssl
* git clone https://wallacepontes-admin@bitbucket.org/entel_fuentes/repo_portgateway_21.git

[Branches com Bitbucket](https://www.atlassian.com/br/git/tutorials/learn-branching-with-bitbucket-cloud)

2. SSL Certificate problem: unable to get local issuer certificate.

* [Unable to resolve "unable to get local issuer certificate" using git on Windows with self-signed certificate](https://stackoverflow.com/questions/23885449/unable-to-resolve-unable-to-get-local-issuer-certificate-using-git-on-windows)
* Just execute: `git config --global http.sslbackend schannel`


## move your branch back one commit

* git status
* git log

Step 1: Revert the branch to the commit before the one you want to remove.

* git reset --hard HEAD~1

This will move your branch back one commit, effectively removing the last commit from your local branch.

Step 2: Force-push the branch to the remote repository

* git push --force origin <branch-name>.


## Ranking de repositórios Github



> 1. [The most popular GitHub repositories, users, and companies](https://gitstar-ranking.com/)
>> - [Developer Roadmaps](https://roadmap.sh/)

[The MOST FAMOUS projects on GitHub ARE NOT software](https://youtu.be/SIA3QfTGnko?si=VqYXGSemXj-VhHIF&t=119)


## Videos

 * [How GitHub Copilot And OpenAI Codex Help Developers Write Code](https://www.youtube.com/watch?v=LEsPuLjwXn0)
	> [<img src="https://img.youtube.com/vi/LEsPuLjwXn0/0.jpg" width="200">](https://www.youtube.com/watch?v=LEsPuLjwXn0 "How GitHub Copilot And OpenAI Codex Help Developers Write Code by DevOps Toolkit 4,389 views 20 minutes")
 * [GitHub Copilot: Coding Will Never Be The Same Again • Ryan J. Salva • YOW! 2023](https://www.youtube.com/watch?v=m0skYNIO3mk)
	> [<img src="https://img.youtube.com/vi/m0skYNIO3mk/0.jpg" width="200">](https://www.youtube.com/watch?v=m0skYNIO3mk "GitHub Copilot: Coding Will Never Be The Same Again • Ryan J. Salva • YOW! 2023 by GOTO Conferences 4,733 views 50 minutes")
 * [Devin AI, Laravel 11, GPT-4 Turbo liberado, Vazamentos no Github, Midjourney vs Stability #141](https://www.youtube.com/watch?v=3H09RDzA0sw)
	> [<img src="https://img.youtube.com/vi/3H09RDzA0sw/0.jpg" width="200">](https://www.youtube.com/watch?v=3H09RDzA0sw "Devin AI, Laravel 11, GPT-4 Turbo liberado, Vazamentos no Github, Midjourney vs Stability #141 by Compilado do Código Fonte TV [OFICIAL] 11,552 views 1 hour, 7 minutes")
 * [How GitHub Copilot And OpenAI Codex Help Developers Write Code](https://www.youtube.com/watch?v=LEsPuLjwXn0)
	> [<img src="https://img.youtube.com/vi/LEsPuLjwXn0/0.jpg" width="200">](https://www.youtube.com/watch?v=LEsPuLjwXn0 "How GitHub Copilot And OpenAI Codex Help Developers Write Code by DevOps Toolkit 4,389 views 20 minutes")
 * [How GitHub Copilot And OpenAI Codex Help Developers Write Code](https://www.youtube.com/watch?v=LEsPuLjwXn0)
	> [<img src="https://img.youtube.com/vi/LEsPuLjwXn0/0.jpg" width="200">](https://www.youtube.com/watch?v=LEsPuLjwXn0 "How GitHub Copilot And OpenAI Codex Help Developers Write Code by DevOps Toolkit 4,389 views 20 minutes")
 * [How GitHub Copilot And OpenAI Codex Help Developers Write Code](https://www.youtube.com/watch?v=LEsPuLjwXn0)
	> [<img src="https://img.youtube.com/vi/LEsPuLjwXn0/0.jpg" width="200">](https://www.youtube.com/watch?v=LEsPuLjwXn0 "How GitHub Copilot And OpenAI Codex Help Developers Write Code by DevOps Toolkit 4,389 views 20 minutes")
 * [The MOST FAMOUS projects on GitHub ARE NOT software](https://www.youtube.com/watch?v=SIA3QfTGnko)
	> [<img src="https://img.youtube.com/vi/SIA3QfTGnko/0.jpg" width="200">](https://www.youtube.com/watch?v=SIA3QfTGnko "The MOST FAMOUS projects on GitHub ARE NOT software by Diolinux 27,669 views 9 minutes, 42 seconds")
 * [Roadmap.sh - Um diamante escondido no GitHub 💎](https://www.youtube.com/watch?v=MTxZl2E5e2g)
	> [<img src="https://img.youtube.com/vi/MTxZl2E5e2g/0.jpg" width="200">](https://www.youtube.com/watch?v=MTxZl2E5e2g "Roadmap.sh - Um diamante escondido no GitHub 💎 by Diolinux 37,927 views 10 minutes, 38 seconds")
 * [The MOST FAMOUS projects on GitHub ARE NOT software](https://www.youtube.com/watch?v=SIA3QfTGnko)
	> [<img src="https://img.youtube.com/vi/SIA3QfTGnko/0.jpg" width="200">](https://www.youtube.com/watch?v=SIA3QfTGnko "The MOST FAMOUS projects on GitHub ARE NOT software by Diolinux 27,669 views 9 minutes, 42 seconds")
 * [Roadmap.sh - Um diamante escondido no GitHub 💎](https://www.youtube.com/watch?v=MTxZl2E5e2g)
	> [<img src="https://img.youtube.com/vi/MTxZl2E5e2g/0.jpg" width="200">](https://www.youtube.com/watch?v=MTxZl2E5e2g "Roadmap.sh - Um diamante escondido no GitHub 💎 by Diolinux 37,927 views 10 minutes, 38 seconds")
 * [Git vs. GitHub: What&#39;s the difference?](https://www.youtube.com/watch?v=wpISo9TNjfU)
	> [<img src="https://img.youtube.com/vi/wpISo9TNjfU/0.jpg" width="200">](https://www.youtube.com/watch?v=wpISo9TNjfU "Git vs. GitHub: What&#39;s the difference? by IBM Technology 362,973 views 10 minutes, 6 seconds")
 * [JACK DORSEY oferece PRÊMIO de 10 BITCOINS para QUEM CRIAR GITHUB PERMISSIONLESS, mas como?](https://www.youtube.com/watch?v=Ge_du0VDJpA)
	> [<img src="https://img.youtube.com/vi/Ge_du0VDJpA/0.jpg" width="200">](https://www.youtube.com/watch?v=Ge_du0VDJpA "JACK DORSEY oferece PRÊMIO de 10 BITCOINS para QUEM CRIAR GITHUB PERMISSIONLESS, mas como? by safesrc 33,528 views 11 minutes, 50 seconds")
 * [Finding Diffs Between Larger Files - How to Use Git and GitHub](https://www.youtube.com/watch?v=MsmbtwibNQU)
	> [<img src="https://img.youtube.com/vi/MsmbtwibNQU/0.jpg" width="200">](https://www.youtube.com/watch?v=MsmbtwibNQU "Finding Diffs Between Larger Files - How to Use Git and GitHub by Udacity 81,986 views 4 minutes, 36 seconds")
 * [Introduction - How to Use Git and GitHub](https://www.youtube.com/watch?v=Ytux4IOAR_s)
	> [<img src="https://img.youtube.com/vi/Ytux4IOAR_s/0.jpg" width="200">](https://www.youtube.com/watch?v=Ytux4IOAR_s "Introduction - How to Use Git and GitHub by Udacity 62,941 views 1 minute, 2 seconds")
 * [Git and GitHub for Beginners - Crash Course](https://www.youtube.com/watch?v=RGOj5yH7evk)
	> [<img src="https://img.youtube.com/vi/RGOj5yH7evk/0.jpg" width="200">](https://www.youtube.com/watch?v=RGOj5yH7evk "Git and GitHub for Beginners - Crash Course by freeCodeCamp.org 3,933,334 views 1 hour, 8 minutes")
 * [Creating Your Repository from the Github Template](https://www.youtube.com/watch?v=8cxYgaMB9ow)
	> [<img src="https://img.youtube.com/vi/8cxYgaMB9ow/0.jpg" width="200">](https://www.youtube.com/watch?v=8cxYgaMB9ow "Creating Your Repository from the Github Template by ExamPro 6,812 views 1 minute, 47 seconds")
 * [Introduction - How to Use Git and GitHub](https://www.youtube.com/watch?v=Ytux4IOAR_s)
	> [<img src="https://img.youtube.com/vi/Ytux4IOAR_s/0.jpg" width="200">](https://www.youtube.com/watch?v=Ytux4IOAR_s "Introduction - How to Use Git and GitHub by Udacity 62,941 views 1 minute, 2 seconds")
 * [Introduction - How to Use Git and GitHub](https://www.youtube.com/watch?v=Ytux4IOAR_s)
	> [<img src="https://img.youtube.com/vi/Ytux4IOAR_s/0.jpg" width="200">](https://www.youtube.com/watch?v=Ytux4IOAR_s "Introduction - How to Use Git and GitHub by Udacity 62,941 views 1 minute, 2 seconds")
 * [Staging Area - How to Use Git and GitHub](https://www.youtube.com/watch?v=t6GMcIoCD9Q)
	> [<img src="https://img.youtube.com/vi/t6GMcIoCD9Q/0.jpg" width="200">](https://www.youtube.com/watch?v=t6GMcIoCD9Q "Staging Area - How to Use Git and GitHub by Udacity 36,770 views 2 minutes, 2 seconds")
 * [Initializing a Repository - How to Use Git and GitHub](https://www.youtube.com/watch?v=PZveoC4c-2s)
	> [<img src="https://img.youtube.com/vi/PZveoC4c-2s/0.jpg" width="200">](https://www.youtube.com/watch?v=PZveoC4c-2s "Initializing a Repository - How to Use Git and GitHub by Udacity 29,519 views 1 minute, 7 seconds")
 * [Lesson 2 Intro - How to Use Git and GitHub](https://www.youtube.com/watch?v=F6tSkw2LgcY)
	> [<img src="https://img.youtube.com/vi/F6tSkw2LgcY/0.jpg" width="200">](https://www.youtube.com/watch?v=F6tSkw2LgcY "Lesson 2 Intro - How to Use Git and GitHub by Udacity 4,900 views 30 seconds")
 * [Checking Out Old Versions Solution - How to Use Git and GitHub](https://www.youtube.com/watch?v=LDsb4zc2GbU)
	> [<img src="https://img.youtube.com/vi/LDsb4zc2GbU/0.jpg" width="200">](https://www.youtube.com/watch?v=LDsb4zc2GbU "Checking Out Old Versions Solution - How to Use Git and GitHub by Udacity 3,937 views 55 seconds")
 * [Checking Out Old Versions of Code - How to Use Git and GitHub](https://www.youtube.com/watch?v=enodgfNvUsc)
	> [<img src="https://img.youtube.com/vi/enodgfNvUsc/0.jpg" width="200">](https://www.youtube.com/watch?v=enodgfNvUsc "Checking Out Old Versions of Code - How to Use Git and GitHub by Udacity 42,990 views 5 minutes, 10 seconds")
 * [Cloning and Exploring The Repo Solution - How to Use Git and GitHub](https://www.youtube.com/watch?v=veiruOagdkk)
	> [<img src="https://img.youtube.com/vi/veiruOagdkk/0.jpg" width="200">](https://www.youtube.com/watch?v=veiruOagdkk "Cloning and Exploring The Repo Solution - How to Use Git and GitHub by Udacity 4,932 views 1 minute, 5 seconds")
 * [Cloning and Exploring The Repo - How to Use Git and GitHub](https://www.youtube.com/watch?v=WQjNhypqwNE)
	> [<img src="https://img.youtube.com/vi/WQjNhypqwNE/0.jpg" width="200">](https://www.youtube.com/watch?v=WQjNhypqwNE "Cloning and Exploring The Repo - How to Use Git and GitHub by Udacity 42,838 views 1 minute, 59 seconds")
 * [Tracking Across Multiple Files Solution - How to Use Git and GitHub](https://www.youtube.com/watch?v=4t8msUHX0PE)
	> [<img src="https://img.youtube.com/vi/4t8msUHX0PE/0.jpg" width="200">](https://www.youtube.com/watch?v=4t8msUHX0PE "Tracking Across Multiple Files Solution - How to Use Git and GitHub by Udacity 5,080 views 50 seconds")
 * [Tracking Across Multiple Files - How to Use Git and GitHub](https://www.youtube.com/watch?v=Rx4PIZiYAl4)
	> [<img src="https://img.youtube.com/vi/Rx4PIZiYAl4/0.jpg" width="200">](https://www.youtube.com/watch?v=Rx4PIZiYAl4 "Tracking Across Multiple Files - How to Use Git and GitHub by Udacity 33,758 views 1 minute, 11 seconds")
 * [Concept Map: diff Solution - How to Use Git and GitHub](https://www.youtube.com/watch?v=-8gvW51AywA)
	> [<img src="https://img.youtube.com/vi/-8gvW51AywA/0.jpg" width="200">](https://www.youtube.com/watch?v=-8gvW51AywA "Concept Map: diff Solution - How to Use Git and GitHub by Udacity 6,043 views 29 seconds")
 * [Properties of a VCS for Code Solution - How to Use Git and GitHub](https://www.youtube.com/watch?v=LtEkcxNqQCU)
	> [<img src="https://img.youtube.com/vi/LtEkcxNqQCU/0.jpg" width="200">](https://www.youtube.com/watch?v=LtEkcxNqQCU "Properties of a VCS for Code Solution - How to Use Git and GitHub by Udacity 6,629 views 1 minute, 8 seconds")
 * [Properties of a VCS for Code - How to Use Git and GitHub](https://www.youtube.com/watch?v=ynL0pIK0kVE)
	> [<img src="https://img.youtube.com/vi/ynL0pIK0kVE/0.jpg" width="200">](https://www.youtube.com/watch?v=ynL0pIK0kVE "Properties of a VCS for Code - How to Use Git and GitHub by Udacity 39,349 views 1 minute, 34 seconds")
 * [Finding Diffs Solution - How to Use Git and GitHub](https://www.youtube.com/watch?v=StbL9767tsE)
	> [<img src="https://img.youtube.com/vi/StbL9767tsE/0.jpg" width="200">](https://www.youtube.com/watch?v=StbL9767tsE "Finding Diffs Solution - How to Use Git and GitHub by Udacity 9,577 views 1 minute, 14 seconds")
 * [Finding Diffs Between Larger Files - How to Use Git and GitHub](https://www.youtube.com/watch?v=MsmbtwibNQU)
	> [<img src="https://img.youtube.com/vi/MsmbtwibNQU/0.jpg" width="200">](https://www.youtube.com/watch?v=MsmbtwibNQU "Finding Diffs Between Larger Files - How to Use Git and GitHub by Udacity 81,986 views 4 minutes, 36 seconds")
 * [Differences Between Two Files Solution - How to Use Git and GitHub](https://www.youtube.com/watch?v=a7hifhLsWH4)
	> [<img src="https://img.youtube.com/vi/a7hifhLsWH4/0.jpg" width="200">](https://www.youtube.com/watch?v=a7hifhLsWH4 "Differences Between Two Files Solution - How to Use Git and GitHub by Udacity 15,560 views 40 seconds")
 * [Differences Between Two Files - How to Use Git and GitHub](https://www.youtube.com/watch?v=PO5IwZqFdMc)
	> [<img src="https://img.youtube.com/vi/PO5IwZqFdMc/0.jpg" width="200">](https://www.youtube.com/watch?v=PO5IwZqFdMc "Differences Between Two Files - How to Use Git and GitHub by Udacity 79,236 views 46 seconds")
 * [Introduction - How to Use Git and GitHub](https://www.youtube.com/watch?v=Ytux4IOAR_s)
	> [<img src="https://img.youtube.com/vi/Ytux4IOAR_s/0.jpg" width="200">](https://www.youtube.com/watch?v=Ytux4IOAR_s "Introduction - How to Use Git and GitHub by Udacity 62,941 views 1 minute, 2 seconds")
 * [Git and GitHub for Beginners - Crash Course](https://www.youtube.com/watch?v=RGOj5yH7evk)
	> [<img src="https://img.youtube.com/vi/RGOj5yH7evk/0.jpg" width="200">](https://www.youtube.com/watch?v=RGOj5yH7evk "Git and GitHub for Beginners - Crash Course by freeCodeCamp.org 3,933,334 views 1 hour, 8 minutes")
 * [Como Um Garoto do Ensino Médio Hackeou o GitHub [Análise Detalhada]](https://www.youtube.com/watch?v=O7M_d46Zhxo)
	> [<img src="https://img.youtube.com/vi/O7M_d46Zhxo/0.jpg" width="200">](https://www.youtube.com/watch?v=O7M_d46Zhxo "Como Um Garoto do Ensino Médio Hackeou o GitHub [Análise Detalhada] by Filipe Deschamps 499,029 views 14 minutes, 53 seconds")

### Git

 * [A nova corrida do ouro no mercado digital | SaaS + No-code](https://www.youtube.com/watch?v=kUES8gmTxUQ)
	> [<img src="https://img.youtube.com/vi/kUES8gmTxUQ/0.jpg" width="200">](https://www.youtube.com/watch?v=kUES8gmTxUQ "A nova corrida do ouro no mercado digital | SaaS + No-code by NordKraken 11,054 views 13 minutes, 8 seconds")
 * [Gitea - Keep Your Repo Private At Home!](https://www.youtube.com/watch?v=VU-K4djix7Y)
	> [<img src="https://img.youtube.com/vi/VU-K4djix7Y/0.jpg" width="200">](https://www.youtube.com/watch?v=VU-K4djix7Y "Gitea - Keep Your Repo Private At Home! by Jim&#39;s Garage 30,763 views 12 minutes, 20 seconds")
 * [Git Branches Tutorial](https://www.youtube.com/watch?v=e2IbNHi4uCI)
	> [<img src="https://img.youtube.com/vi/e2IbNHi4uCI/0.jpg" width="200">](https://www.youtube.com/watch?v=e2IbNHi4uCI "Git Branches Tutorial by freeCodeCamp.org 224,269 views 33 minutes")
 * [git - Replace branch master with other branch | Make an old commit to New Commit |Old Commit to HEAD](https://www.youtube.com/watch?v=DU712NT6IqY)
	> [<img src="https://img.youtube.com/vi/DU712NT6IqY/0.jpg" width="200">](https://www.youtube.com/watch?v=DU712NT6IqY "git - Replace branch master with other branch | Make an old commit to New Commit |Old Commit to HEAD by LinuXamination 1,869 views 10 minutes, 55 seconds")
 * [Git 3: Moving between Commits](https://www.youtube.com/watch?v=H-YK_CCs7Mc)
	> [<img src="https://img.youtube.com/vi/H-YK_CCs7Mc/0.jpg" width="200">](https://www.youtube.com/watch?v=H-YK_CCs7Mc "Git 3: Moving between Commits by Younmin Bae 540 views 7 minutes, 22 seconds")
 * [How to Switch Between Commits in Git - an Easy Guide || ForTheGeeks](https://www.youtube.com/watch?v=tyu2PahJJ6Y)
	> [<img src="https://img.youtube.com/vi/tyu2PahJJ6Y/0.jpg" width="200">](https://www.youtube.com/watch?v=tyu2PahJJ6Y "How to Switch Between Commits in Git - an Easy Guide || ForTheGeeks by For the Geeks 539 views 1 minute, 24 seconds")
 * [EXISTE UMA NOVA PLATAFORMA PARA REPOSITÓRIOS GIT!](https://www.youtube.com/watch?v=Gqq7eDFisjI)
	> [<img src="https://img.youtube.com/vi/Gqq7eDFisjI/0.jpg" width="200">](https://www.youtube.com/watch?v=Gqq7eDFisjI "EXISTE UMA NOVA PLATAFORMA PARA REPOSITÓRIOS GIT! by Código Fonte TV 34,016 views 19 minutes")
 * [EXISTE UMA NOVA PLATAFORMA PARA REPOSITÓRIOS GIT!](https://www.youtube.com/watch?v=Gqq7eDFisjI)
	> [<img src="https://img.youtube.com/vi/Gqq7eDFisjI/0.jpg" width="200">](https://www.youtube.com/watch?v=Gqq7eDFisjI "EXISTE UMA NOVA PLATAFORMA PARA REPOSITÓRIOS GIT! by Código Fonte TV 34,016 views 19 minutes")
 * [Gitlab Project Management: Sprints, User Stories, and Tasks](https://www.youtube.com/watch?v=ZBjCmOYNb5Q)
	> [<img src="https://img.youtube.com/vi/ZBjCmOYNb5Q/0.jpg" width="200">](https://www.youtube.com/watch?v=ZBjCmOYNb5Q "Gitlab Project Management: Sprints, User Stories, and Tasks by Benjamin Garrard 28,600 views 10 minutes, 23 seconds")
 * [Gitlab Project Management: Sprints, User Stories, and Tasks](https://www.youtube.com/watch?v=ZBjCmOYNb5Q)
	> [<img src="https://img.youtube.com/vi/ZBjCmOYNb5Q/0.jpg" width="200">](https://www.youtube.com/watch?v=ZBjCmOYNb5Q "Gitlab Project Management: Sprints, User Stories, and Tasks by Benjamin Garrard 28,600 views 10 minutes, 23 seconds")
 * [Gitlab Project Management: Sprints, User Stories, and Tasks](https://www.youtube.com/watch?v=ZBjCmOYNb5Q)
	> [<img src="https://img.youtube.com/vi/ZBjCmOYNb5Q/0.jpg" width="200">](https://www.youtube.com/watch?v=ZBjCmOYNb5Q "Gitlab Project Management: Sprints, User Stories, and Tasks by Benjamin Garrard 28,600 views 10 minutes, 23 seconds")
 * [Como clonar/copiar apenas um arquivo ou diretório do repositório remoto git | Code Pitch #3](https://www.youtube.com/watch?v=zwxMn44TWq0)
	> [<img src="https://img.youtube.com/vi/zwxMn44TWq0/0.jpg" width="200">](https://www.youtube.com/watch?v=zwxMn44TWq0 "Como clonar/copiar apenas um arquivo ou diretório do repositório remoto git | Code Pitch #3 by Angelo Luz 6,812 views 6 minutes, 12 seconds")
 * [Liberdade de Expressão e internet: Limites dos usuários e plataformas e Atuação em Direito Digital](https://www.youtube.com/watch?v=d8vxaO38FO8)
	> [<img src="https://img.youtube.com/vi/d8vxaO38FO8/0.jpg" width="200">](https://www.youtube.com/watch?v=d8vxaO38FO8 "Liberdade de Expressão e internet: Limites dos usuários e plataformas e Atuação em Direito Digital by Prática em Direito Digital 1,134 views 1 hour, 27 minutes")
 * [Git Branches Tutorial](https://www.youtube.com/watch?v=e2IbNHi4uCI)
	> [<img src="https://img.youtube.com/vi/e2IbNHi4uCI/0.jpg" width="200">](https://www.youtube.com/watch?v=e2IbNHi4uCI "Git Branches Tutorial by freeCodeCamp.org 224,272 views 33 minutes")
 * [Google Cloud Digital Leader Certification Course - Pass the Exam!](https://www.youtube.com/watch?v=UGRDM86MBIQ)
	> [<img src="https://img.youtube.com/vi/UGRDM86MBIQ/0.jpg" width="200">](https://www.youtube.com/watch?v=UGRDM86MBIQ "Google Cloud Digital Leader Certification Course - Pass the Exam! by freeCodeCamp.org 709,149 views 6 hours, 6 minutes")
 * [Git for Professionals Tutorial - Tools &amp; Concepts for Mastering Version Control with Git](https://www.youtube.com/watch?v=Uszj_k0DGsg)
	> [<img src="https://img.youtube.com/vi/Uszj_k0DGsg/0.jpg" width="200">](https://www.youtube.com/watch?v=Uszj_k0DGsg "Git for Professionals Tutorial - Tools &amp; Concepts for Mastering Version Control with Git by freeCodeCamp.org 1,570,921 views 40 minutes")
 * [Advanced Git Tutorial - Interactive Rebase, Cherry-Picking, Reflog, Submodules and more](https://www.youtube.com/watch?v=qsTthZi23VE)
	> [<img src="https://img.youtube.com/vi/qsTthZi23VE/0.jpg" width="200">](https://www.youtube.com/watch?v=qsTthZi23VE "Advanced Git Tutorial - Interactive Rebase, Cherry-Picking, Reflog, Submodules and more by freeCodeCamp.org 233,057 views 34 minutes")
 * [Full Gitpod Course – ExamPro Cloud Developer Environment Certification](https://www.youtube.com/watch?v=XcjqapXfrhk)
	> [<img src="https://img.youtube.com/vi/XcjqapXfrhk/0.jpg" width="200">](https://www.youtube.com/watch?v=XcjqapXfrhk "Full Gitpod Course – ExamPro Cloud Developer Environment Certification by freeCodeCamp.org 54,285 views 12 hours")
 * [Git for Professionals Tutorial - Tools &amp; Concepts for Mastering Version Control with Git](https://www.youtube.com/watch?v=Uszj_k0DGsg)
	> [<img src="https://img.youtube.com/vi/Uszj_k0DGsg/0.jpg" width="200">](https://www.youtube.com/watch?v=Uszj_k0DGsg "Git for Professionals Tutorial - Tools &amp; Concepts for Mastering Version Control with Git by freeCodeCamp.org 1,570,923 views 40 minutes")
 * [Git Forking &amp; Fetch: How to Keep your Fork in Sync with an Upstream Repository](https://www.youtube.com/watch?v=deEYHVpE1c8)
	> [<img src="https://img.youtube.com/vi/deEYHVpE1c8/0.jpg" width="200">](https://www.youtube.com/watch?v=deEYHVpE1c8 "Git Forking &amp; Fetch: How to Keep your Fork in Sync with an Upstream Repository by Faraday Academy 52,025 views 10 minutes, 19 seconds")
 * [GitLab CI CD Tutorial for Beginners [Crash Course]](https://www.youtube.com/watch?v=qP8kir2GUgo)
	> [<img src="https://img.youtube.com/vi/qP8kir2GUgo/0.jpg" width="200">](https://www.youtube.com/watch?v=qP8kir2GUgo "GitLab CI CD Tutorial for Beginners [Crash Course] by TechWorld with Nana 1,065,717 views 1 hour, 9 minutes")
 * [Git Workspace](https://www.youtube.com/watch?v=XPOzPrahXgw)
	> [<img src="https://img.youtube.com/vi/XPOzPrahXgw/0.jpg" width="200">](https://www.youtube.com/watch?v=XPOzPrahXgw "Git Workspace by Udacity 6,922 views 1 minute, 19 seconds")
 * [Open Digital Framework (ODF) Overview  training course](https://www.youtube.com/watch?v=0XZ1nLKJ7eU)
	> [<img src="https://img.youtube.com/vi/0XZ1nLKJ7eU/0.jpg" width="200">](https://www.youtube.com/watch?v=0XZ1nLKJ7eU "Open Digital Framework (ODF) Overview  training course by TM Forum 3,978 views 2 minutes, 28 seconds")
 * [Telia’s OSS/BSS evolution toward 5G digital service delivery ambitions](https://www.youtube.com/watch?v=4yQTcU-MEH0)
	> [<img src="https://img.youtube.com/vi/4yQTcU-MEH0/0.jpg" width="200">](https://www.youtube.com/watch?v=4yQTcU-MEH0 "Telia’s OSS/BSS evolution toward 5G digital service delivery ambitions by TM Forum 364 views 6 minutes, 48 seconds")
 * [Git Commits Across Multiple Files](https://www.youtube.com/watch?v=kBOXmGll8N0)
	> [<img src="https://img.youtube.com/vi/kBOXmGll8N0/0.jpg" width="200">](https://www.youtube.com/watch?v=kBOXmGll8N0 "Git Commits Across Multiple Files by Udacity 7,888 views 2 minutes, 51 seconds")
 * [Using Git to View History](https://www.youtube.com/watch?v=w1JOF67Kaew)
	> [<img src="https://img.youtube.com/vi/w1JOF67Kaew/0.jpg" width="200">](https://www.youtube.com/watch?v=w1JOF67Kaew "Using Git to View History by Udacity 8,068 views 2 minutes, 20 seconds")
 * [Manual Commits in Git](https://www.youtube.com/watch?v=zrpkdHVSG-0)
	> [<img src="https://img.youtube.com/vi/zrpkdHVSG-0/0.jpg" width="200">](https://www.youtube.com/watch?v=zrpkdHVSG-0 "Manual Commits in Git by Udacity 7,879 views 1 minute, 55 seconds")
 * [Git Workspace](https://www.youtube.com/watch?v=XPOzPrahXgw)
	> [<img src="https://img.youtube.com/vi/XPOzPrahXgw/0.jpg" width="200">](https://www.youtube.com/watch?v=XPOzPrahXgw "Git Workspace by Udacity 6,922 views 1 minute, 19 seconds")
 * [Git Forking &amp; Fetch: How to Keep your Fork in Sync with an Upstream Repository](https://www.youtube.com/watch?v=deEYHVpE1c8)
	> [<img src="https://img.youtube.com/vi/deEYHVpE1c8/0.jpg" width="200">](https://www.youtube.com/watch?v=deEYHVpE1c8 "Git Forking &amp; Fetch: How to Keep your Fork in Sync with an Upstream Repository by Faraday Academy 52,028 views 10 minutes, 19 seconds")
 * [GitLab CI CD Tutorial for Beginners [Crash Course]](https://www.youtube.com/watch?v=qP8kir2GUgo)
	> [<img src="https://img.youtube.com/vi/qP8kir2GUgo/0.jpg" width="200">](https://www.youtube.com/watch?v=qP8kir2GUgo "GitLab CI CD Tutorial for Beginners [Crash Course] by TechWorld with Nana 1,065,717 views 1 hour, 9 minutes")

## Videos GitOps

 * [Demystifying GitOps: A Beginner-Friendly Explanation | KodeKloud](https://www.youtube.com/watch?v=GlG6Xr2HH1g)
	> [<img src="https://img.youtube.com/vi/GlG6Xr2HH1g/0.jpg" width="200">](https://www.youtube.com/watch?v=GlG6Xr2HH1g "Demystifying GitOps: A Beginner-Friendly Explanation | KodeKloud by KodeKloud 24,047 views 8 minutes, 1 second")
 * [What is GitOps? | GitOps vs DevOps](https://www.youtube.com/watch?v=lI03nh0EmaQ)
	> [<img src="https://img.youtube.com/vi/lI03nh0EmaQ/0.jpg" width="200">](https://www.youtube.com/watch?v=lI03nh0EmaQ "What is GitOps? | GitOps vs DevOps by Containers from the Couch 6,544 views 6 minutes")

## Referências

> 1. git-scm.com
>> - [ProGit book](https://git-scm.com/book/en/v2)
>> - [Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
>> -  [Tracking Branches - ProGit book](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#_tracking_branches)
>> - [Git - Downloads](https://git-scm.com/downloads)
>> - [Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
>> - [Git Tools - Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
>> - [Git Basics - Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
>> - [Git Branching - Rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)

> 2. freecodecamp
>> - [10 Git Commands Every Developer Should Know](https://www.freecodecamp.org/news/10-important-git-commands-that-every-developer-should-know/)
>> - [Git Switch Branch – How to Change the Branch in Git](https://www.freecodecamp.org/news/git-switch-branch/)

> 3. stackoverflow
>> - [What is a tracking branch?](https://stackoverflow.com/questions/4693588/what-is-a-tracking-branch/4697054#4697054)
>> - [When should I create a new branch?](https://stackoverflow.com/questions/15633409/when-should-i-create-a-new-branch#:~:text=You%20should%20create%20a%20new%20branch%20when%20you%27re,reside%20there%20until%20you%20remove%20it%20using%20git.
)
>> - [git push vs git push origin branchname](https://stackoverflow.com/questions/19312622/git-push-vs-git-push-origin-branchname)

> 3. [The most powerful Git client for Mac and Windows | Tower Git Client](https://www.git-tower.com/windows)
> 4. [Git Cheat Sheet | Build5Nines](https://build5nines.com/git-cheat-sheet/)
> 6. [Git tags vs branches: Differences and when to use them](https://circleci.com/blog/git-tags-vs-branches/#:~:text=Tags%20are%20used%20as%20markers,into%20the%20main%20application%20code.)

> 7. YOUTUBE Channels
>> - [Git for Professionals Tutorial - Tools & Concepts for Mastering Version Control with Git - YouTube](https://www.youtube.com/watch?v=Uszj_k0DGsg)
>> - [Git and GitHub for Beginners - Crash Course - YouTube](https://www.youtube.com/watch?v=RGOj5yH7evk&t=49s)
>> - [Introduction - How to Use Git and GitHub - YouTube](https://www.youtube.com/watch?v=Ytux4IOAR_s&list=PLAwxTw4SYaPk8_-6IGxJtD3i2QAu5_s_p)
>> - [Setting Up Your Workspace on Windows - YouTube](https://www.youtube.com/watch?v=IfLhXM4RnB4&t=282s)




https://nvie.com/posts/a-successful-git-branching-model/

http://scottchacon.com/2011/08/31/github-flow.html

https://superuser.com/questions/1020821/how-can-i-create-a-symbolic-link-on-windows-10#:~:text=mklink%20is%20an%20internal%20command%20only,Configuration%5CWindows%20Settings%5CSecurity%20Settings%5CLocal%20Policies%5CUser%20Rights%20Assignment%5C.&text=mklink%20is%20an%20internal,Settings%5CLocal%20Policies%5CUser%20Rights%20Assignment%5C.&text=an%20internal%20command%20only,Configuration%5CWindows%20Settings%5CSecurity%20Settings%5CLocal%20Policies%5CUser



8. https://stackoverflow.com/questions/29028769/factorypath-added-to-gitignore-is-not-taken-into-account
