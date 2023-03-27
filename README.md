# Check signed commits in PR

A GitHub Action that checks the commits of the current PR and fails if it contains unsigned commits. It also places a comment in the PR to inform the author about next steps.

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

## Change PR Comment

The comment that will be placed in the PR upon detecting unsigned commits can be changed using the `comment` field:

```yml
- name: Check signed commits in PR
  uses: 1Password/check-signed-commits-action@v1
  with:
    comment: |
      Customized comment in the PR
```
