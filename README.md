# Shared GitHub Workflows

This repository centralizes shared GitHub Actions workflows. Currently it contains the Discord notifications workflow that listens to pushes, issues, PRs, comments, reviews, and a manual trigger.

## Usage
- Secrets: by default the workflow reads `DISCORD_WEBHOOK_URL`. To use a different secret name, set repo variable `DISCORD_WEBHOOK_SECRET_NAME` to the desired secret key and add that secret to the repo.
- Triggers: push to `main`/`master`, issue/PR/review events, and `workflow_dispatch` (with optional `commit_sha`).
- Location: subtree the repo directly into `.github/workflows` so GitHub discovers the workflow at `.github/workflows/discord-notifications.yml`.

## Subtree commands
Replace `<remote>` with the remote/URL for this repo (local path or GitHub remote) and run from a consumer repo.

```sh
git remote add shared-githubworkflows <remote>
# First add
git subtree add --prefix .github/workflows shared-githubworkflows main --squash
# To pull updates later
git subtree pull --prefix .github/workflows shared-githubworkflows main --squash
```
