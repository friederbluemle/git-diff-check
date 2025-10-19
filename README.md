# git-diff-check

A simple GitHub Action that checks the repository for whitespace errors using
`git diff --check` against the empty tree.

## Usage

```yaml
name: ci
on: [ push, pull_request ]
jobs:
  whitespace:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: fbactions/git-diff-check@v1
```

## How it works

Runs:

```
git -c core.whitespace=fix,-indent-with-non-tab,trailing-space,cr-at-eol diff --check 4b825dc642cb6eb9a060e54bf8d69288fbee4904
```

This fails the job if whitespace issues are found.
