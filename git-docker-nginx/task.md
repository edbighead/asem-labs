# nginx/docker/git exam

### Git
* [Create a repository](https://help.github.com/en/github/getting-started-with-github/create-a-repo)
* [Clone the repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository)
* [Setting your username in Git](https://help.github.com/en/github/using-git/setting-your-username-in-git)
* [Setting your commit email address in Git](https://help.github.com/en/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address#setting-your-commit-email-address-in-git)
* [Invite to collaborators](https://help.github.com/en/github/setting-up-and-managing-your-github-user-account/inviting-collaborators-to-a-personal-repository) the following people: **edbighead** and **rtudvasev**
* Add **index.html** (find below) file to repository
  * [git add](https://www.atlassian.com/git/tutorials/saving-changes)
  * [git commit](https://www.atlassian.com/git/tutorials/saving-changes/git-commit)
  * [git push](https://www.atlassian.com/git/tutorials/syncing/git-push)

```
<!doctype html>
<html lang="en">
  <head>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">
    <title>Exam lab</title>
  </head>
  <body>
  <div class="container">
    <nav class="navbar navbar-expand-lg navbar-dark bg-danger">
      <a class="navbar-brand" href="#">ASEM</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav">
          <a class="nav-item nav-link active" href="#">Home <span class="sr-only">(current)</span></a>
          <a class="nav-item nav-link" href="#">News</a>
          <a class="nav-item nav-link" href="#">Lectures</a>
        </div>
      </div>
    </nav>
    <div class="d-flex justify-content-center mt-5">
      <h1>Hello, world!</h1>
    </div>
  </div>
  </body>
</html>
```

* [Create a new branch](https://www.atlassian.com/git/tutorials/using-branches/git-checkout)
* Change navbar color `bg-danger`->`bg-success`
* Push your branch with the changes
* [Open a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) and add  **edbighead** and **rtudvasev** to reviewers
* Wait for approve and [merge](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/merging-a-pull-request) it

### Docker
* Run `edbighead/asem-exam` image, mapping local `8081` port to container `80` port
  * [docker run](https://docs.docker.com/engine/reference/run/)
* Enter the running container with [docker exec](https://docs.docker.com/engine/reference/commandline/exec/) command
* [Git clone](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository) your repository

### Nginx
* Access `localhost:8081` in browser
* Doesn't work? ¯\\\_(ツ)\_/¯
* Fix it by editing `/etc/nginx/conf.d/website.conf` file
* Don't forget to [reload](http://nginx.org/en/docs/beginners_guide.html#control) after changing the configuration
---
### Advanced
* Edit `Dockerfile` and `conf.d/website.conf` to make it work out of the box
* Build and push the image