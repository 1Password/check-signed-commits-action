# Check signed commits in PR

A GitHub Action that checks the commits of the current PR and fails if it contains unsigned commits. It also places a comment in the PR to inform the author about next steps.

## Usage

```yml
name: Check signed commits in PR 
on: pull_request_target

jobs:
  check-signed-commits:
    name: Check signed commits in PR
    runs-on: ubuntu-latest
    permissions:
      contents: read
      pull-requests: write
    steps:
      - name: Check signed commits in PR
        uses: 1Password/check-signed-commits-action@v1
```

## `pull_request_target` vs. `pull_request`

Workflows containing this action can be configured to run both on [`pull_request`](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#pull_request) events as on [`pull_request_target`](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#pull_request_target) events.

The reason to prefer `pull_request_target` over `pull_request` is to allow the action to post comments on external PRs created from forks. The GitHub token that comes with the regular `pull_request` event does not support commenting on PRs in the upstream repo.

 When using `pull_request_target`, make sure to set the right permissions in the workflow:

```yml
permissions:
  contents: read
  pull-requests: write
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
