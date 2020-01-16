### Task
Fork the following repository [java-spring-sample-app](https://github.com/edbighead/java-spring-sample-app)

### Pull Request workflow
* Has a name defined
* Starts when on any pull request change
* Runs on ubuntu-latest
* Uses [checkout action](https://github.com/actions/checkout)
* Uses [setup-java action](https://github.com/actions/setup-java) to install `Java 8.0.192`
* Runs unit tests with the following command `mvn clean test --file pom.xml`

### Merge workflow
* Has a name defined
* Starts when something is pushed to `master` branch
* Runs on ubuntu-latest
* Builds and publishes docker image
    ```
    docker login docker.pkg.github.com --username your_github_username --password ${{ secrets.GITHUB_TOKEN }}
    docker build . --tag docker.pkg.github.com/your_github_username/java-spring-sample-app/java-app:latest
    docker push docker.pkg.github.com/your_github_username/java-spring-sample-app/java-app:latest
    ```

### Advanced
* Setup pull request workflow to run on different java versions (8.0.192, 9.0.x, 10). Hint: use [matrix](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions#jobsjob_idstrategymatrix)
* Setup maven dependency caching with [cache action](https://github.com/actions/cache/blob/master/examples.md#java---maven)
* Look for any other actions on [marketplace](https://github.com/marketplace?type=actions)
  * Send telegram notification
  * Send slack notification
  * Post twitter message