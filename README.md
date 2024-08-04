# Setup Git &nbsp; [![Actions](https://img.shields.io/badge/qoomon-GitHub%20Actions-blue)](https://github.com/qoomon/actions)
This GitHub Action will automatically setup following git configs to be ready for `git commit` and `git push` commands
- User Config
  - `user.name` value depends on [`user`](#inputs)input field
  - `user.email` value depends on [`user`](#inputs) input field
- **Push Config**
  - `push.autoSetupRemote` = `true`

# Inputs
- `user` valid values
  - `bot` _(default)_ - configure `github-actions[bot]` as git user
  - `actor` - configure [github actions context](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context) `github.actor` as git user
  - `committer` - configure committer from `HEAD` commit as git user
  - `USER_NAME <USER_EMAIL>` - configure git user explicitly

### Example
```yaml
jobs:
  example:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: qoomon/actions--setup-git@v1
        with:
          user: bot

      - run: |
          date > dummy.txt
          git add dummy.txt
          git commit -m "chore: update dummy"
          git push
```

## Development

### Release New Action Version

Trigger [Release Version workflow](/actions/workflows/action-release.yaml)
