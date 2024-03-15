# Setup GIT
GitHub Action to setup git user config and push config

### User Config
- `git config --global user.name 'github-actions[bot]'`
- `git config --global user.email '41898282+github-actions[bot]@users.noreply.github.com'`

Actual values depends on `user` input
- `bot` _(default)_ - configure `github-actions[bot]` as git user
- `actor` - configure [github actions context](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context) `github.actor` as git user
- `committer` - configure committer from `HEAD` commit as git user

### Push Config           
- `git config --global push.autoSetupRemote true`

### Example
```yaml
jobs:
  basic-ubuntu-20:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: qoomon/setup-git@v1

      - runs: |
          date > dummy.txt
          git add dummy.txt
          git commit -m "chore: update dummy"
          git push
```

### Inputs
```yaml
inputs:
  user:
    description: User to setup bot (github-actions[bot]), actor (github.actor) or commit (user from `HEAD` commit)
    required: true
    default: 'bot'
```

## Development

### Release New Action Version

Trigger [Release Version workflow](/actions/workflows/action-release.yaml)
