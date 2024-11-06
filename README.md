# Pre-commit hooks for your bug & issue tracker #

### Using pre-commit-hooks with pre-commit ###


Add the following to your `.pre-commit-config.yaml`:
```
  - repo: https://github.com/redwerk/prehooks
    rev: 1.0.0
    hooks:
      - id: task_id-in-branch-name
      - id: add-msg-issue-prefix
```

### Available Hooks ###

___task_id-in-branch-name___

Ensures that branches contain an issue ID.

* The branch name must match the following regex pattern: `(^[0-9A-Za-z_]+-[0-9]+)\/[a-zA-Z0-9._-]+$`. 
* Example: `PROJ-123/short_description`

* The following branch names are whitelisted: `'master', 'main', 'staging', 'develop', 'dev', 'stg'`

___add-msg-issue-prefix___

Searches for a Jira-like issue ID in the branch name and prepends it to the commit message.

* The issue ID is taken from the branch name and added to the commit message.

* Example: if your commit message is: `added some important logic` and your branch is: `PROJ-123/short_description` , the hook will modify commit message to: `[PROJ-123] added some important logic`

### Troubleshooting ###

If you've enabled `add-msg-issue-prefix` in your `.pre-commit-config.yaml` but it doesn't seem to work, check whether the `prepare-commit-msg` hook type is installed by running:
`pre-commit install --hook-type prepare-commit-msg`


