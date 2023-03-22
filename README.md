# Check signed commits in PR

A GitHub Action that checks the commits of the current PR and fails if there are 1 or more unsigned commits. It also adds a comment to the PR that links to the [1Password Commit Signing docs](https://developer.1password.com/docs/ssh/git-commit-signing/).

## Usage

```yml
name: Check signed commits in PR 
on: pull_request

jobs:
  build:
    name: Check signed commits in PR 
    runs-on: ubuntu-latest
    steps:
      - name: Check out code
        uses: actions/checkout@v3

      - name: Check signed commits in PR
        uses: 1Password/check-signed-commits-action@v1
```
