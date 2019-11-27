# GIT

### Initial setup
* [Generating a new SSH key](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
* [Adding a new SSH key to your GitHub account](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)
* Split into teams (3-4 people). Every person picks a letter **(A, B, C, D)**, these will be used when distributing tasks
*  [Create a new repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-new-repository)
* [Mirror](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/duplicating-a-repository#mirroring-a-repository) existing [asem-labs-web](https://github.com/edbighead/asem-labs-web) repository to your newly created repo in previous step
* [Configuring protected branches](https://help.github.com/en/github/administering-a-repository/configuring-protected-branches) - protect **master** branch by restricting pushes without pull request and enabling mandatory reviews
* [Inviting collaborators to a personal repository](https://help.github.com/en/github/setting-up-and-managing-your-github-user-account/inviting-collaborators-to-a-personal-repository) - invite your teammates to your repository
* **Choose one person** on whose repository you all will be working and clone it
* **Congratulations!** This will be your software development team

### Splitting tasks
* [Create a new branch](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) with name **feature/n**, where **n** is your *letter* (ex. **feature/D**). Pick a task from the table below. [Commit](https://git-scm.com/docs/git-commit) your changes. [Push](https://git-scm.com/docs/git-push) your branch

| member  | task          
| ------- | -------
| A       | change **GET STARTED** button text and color
| B       | change footer color and **Get In Touch** text to **Contact Us**
| C       | change **3 bottom images** to something winter-ish
| D       | change the **phone image** to ASEM logo and surrounding quotes to your favourite programming languages

* [Create a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) with your changes. Ask your colleagues to review it and [merge](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/merging-a-pull-request) it

**Note: Don't forget to [pull](https://git-scm.com/docs/git-pull) your colleagues changes before starting next task**

### Solving conflicts
* After pulling changes from the previous task, everyone should create a **new branch** with name **feature/your-real-name** (ex. feature/ed)
* Everyone should change the email in **Contact Us** section (*information@untitled.tld*) to some random email. Commit your changes, push your branch and open a pull request
* Start merging pull requests one by one
* Conflicts!
* Pull changes that were merged to master branch. Switch back to your branch and [rebase](https://git-scm.com/docs/git-rebase) it to master
* [Resolving merge conflicts after a Git rebase](https://help.github.com/en/github/using-git/resolving-merge-conflicts-after-a-git-rebase)

**Note: Don't forget to [pull](https://git-scm.com/docs/git-pull) your colleagues changes before starting next task**

### Tagging and reverting changes
* After pulling changes from the previous task, everyone should [create and push tag](https://git-scm.com/book/en/v2/Git-Basics-Tagging) with the following name **n.0.1** where *n* is your letter (ex. A.0.1).
* Create a branch named **release/n.0** where *n* is your letter (ex. release/A.0). Push your branch.
* Create a new branch from **release/n.0**. [Revert](https://git-scm.com/docs/git-revert) a random change that was made in **Splitting tasks** task. Open a pull request to **release/n.0** branch. Merge it.
* Pull changes after merge. Create and push a new tag **n.0.2**

### Squashing
**Note: Don't forget to [pull](https://git-scm.com/docs/git-pull) your colleagues changes before starting next task**
* Create a new branch from **master**. Branch name is up to you
* Modify *index.html* page 3 times, creating 3 commits.
* Open a PR with your commits.
* [Squash](https://github.com/wprig/wprig/wiki/How-to-squash-commits) your commits. Push your changes and merge the pull request.

### Resources
* [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
* [Pro Git](https://git-scm.com/book/en/v2)

