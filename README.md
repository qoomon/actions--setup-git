# setup-git-user
GitHub Action to setup git user config

### Example
```yaml
jobs:

  basic-ubuntu-20:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: qoomon/setup-git-user

      - runs: |
          date > dummy.txt
          git add dummy.txt
          git commit -m "chore: update dummy"
          git push
```

### Inputs

- `user` - select user to setup
  - `bot` _(default)_ - configure `github-actions[bot]` as git user
  - `actor` - configure [github actions context](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context) `github.actor` as git user
  - `commit` - configure user from `HEAD` commit as git user
