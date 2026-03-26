# .github

Organization-wide defaults for [Techne Analytics](https://github.com/Techne-Analytics) repositories.

## What's in here

| Path | Purpose |
|------|---------|
| `profile/README.md` | Organization profile (visible at github.com/Techne-Analytics) |
| `CONTRIBUTING.md` | Default contributing guide inherited by all repos |
| `CODE_OF_CONDUCT.md` | Code of conduct |
| `SECURITY.md` | Vulnerability reporting process |
| `.github/ISSUE_TEMPLATE/` | Issue templates (bug, feature, task) |
| `.github/PULL_REQUEST_TEMPLATE.md` | Default PR template |
| `.github/PULL_REQUEST_TEMPLATE/release.md` | Release PR template |
| `.github/release.yml` | Auto-generated release notes categories |
| `.github/labels.yml` | Canonical label set synced to all repos |
| `.github/workflows/label-sync.yml` | Syncs labels.yml to repos on push |
| `CLAUDE.md` | Claude Code instructions for this repo |

## How org defaults work

GitHub automatically applies files from this repo as defaults for any Techne-Analytics repo that doesn't define its own. Repos can override any file by creating their own version.

See [GitHub docs: creating a default community health file](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file).
