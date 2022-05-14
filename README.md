# reusable-workflows-demo

This repo contains demo reusable workflows which can be used to build, test, and (optionally) run a security scan on your go source code.  For more information on how it works see this [blog post]().

# Warning
This is an example of the reusable workflow technology, and as such may not be the best go workflows ever written.  If you do use them, and they do something insecure, please let me know, and I'll work to correct it, but these are offered as a technical example and shouldn't be considered production ready in their current state.

# Workflows
## reusable-go-build-test-scan-simple
This action compiles your project with the input version of `go`, runs unit tests, and (optionally) scans the code with SonarCloud as well as Snyk.io if the required credentials are provided.

## reusable-go-build-test-scan-advanced
While this performs the same actions as reusable-go-build-test-scan-simple, this leverages composite actions which gives the following advantages:
1. Your code can be more modular limiting the number of parts that are copied and pasted between workflows
2. Users don't need to adopt your workflows 100% of the time which in large organizations may take time.  Instead, they can take advantage of these existing actions and leverage them in existing workflows which reduces the burden for them to create workflows.

However the disadvantage of this is that because of the way the actions are referenced, it requires adding a commit every time you create a new release, this is taken care of by the `internal-create-release` workflow.

## internal-create-release
Designed to be run within this repo as a manual step to cut a new release allowing you to easily release the latest commit of `main` as a new release.
