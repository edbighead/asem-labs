## Github Actions

### CI/CD

## [About continuous integration](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/about-continuous-integration#about-continuous-integration)

Continuous integration (CI) is a **software practice** that requires **frequently committing** code to a shared repository. Committing code more often **detects errors sooner** and **reduces the amount of code a developer needs to debug** when finding the source of an error. Frequent code updates also make it easier to **merge changes from different members** of a software development team. This is great for developers, who can spend more time writing code and less time debugging errors or resolving merge conflicts.

When you commit code to your repository, you can continuously build and test the code to make sure that the commit doesn't introduce errors. Your tests can include code linters (which check style formatting), security checks, code coverage, functional tests, and other custom checks.

Building and testing your code requires a server. You can build and test updates locally before pushing code to a repository, or you can use a CI server that checks for new code commits in a repository.

## [About continuous integration using GitHub Actions](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/about-continuous-integration#about-continuous-integration-using-github-actions)
CI using GitHub Actions offers workflows that can build the code in your repository and run your tests. Workflows can run on GitHub-hosted virtual machines, or on machines that you host yourself.

You can configure your CI workflow to run when a GitHub event occurs (for example, when new code is pushed to your repository), on a set schedule, or when an external event occurs using the repository dispatch webhook.

GitHub runs your CI tests and provides the results of each test in the pull request, so you can see whether the change in your branch introduces an error. When all CI tests in a workflow pass, the changes you pushed are ready to be reviewed by a team member or merged. When a test fails, one of your changes may have caused the failure.

### [Virtual environments for GitHub-hosted runners](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/virtual-environments-for-github-hosted-runners)


### [Software installed on GitHub-hosted runners](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/software-installed-on-github-hosted-runners)

### [Workflow syntax for GitHub Actions](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions)


## Required blocks
* ### [name](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions#name)
* ### [on](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions#on)
  * ### [events that trigger workflows](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/events-that-trigger-workflows#about-workflow-events)
* ### [runs-on](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions#jobsjob_idruns-on)
## Other useful blocks
* ### [steps](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions#jobsjob_idsteps)
* ### [uses](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions#jobsjob_idsteps) 
  * ### [marketplace](https://github.com/marketplace?type=actions)
 * ### [run](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions#jobsjob_idstepsrun)

### [Using environment variables](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/using-environment-variables)
### [Authenticating with the GITHUB_TOKEN](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/authenticating-with-the-github_token)
### [Caching dependencies to speed up workflows](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/caching-dependencies-to-speed-up-workflows)