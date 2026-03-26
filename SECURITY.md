# Security Policy

## Reporting a vulnerability

If you discover a security vulnerability in any Techne Analytics repository, please report it responsibly.

**Do not open a public issue.**

Instead, email **security@techneanalytics.com** with:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if you have one)

We will acknowledge your report within 48 hours and provide a timeline for resolution.

## Supported versions

Only the latest release of each repository is actively maintained. If you're using an older version, please upgrade before reporting.

## Security practices

All Techne Analytics repositories follow these baseline practices:
- No secrets, credentials, or API keys in source code
- `.env`, `.pem`, and `.key` files are blocked from commits
- Dependencies are reviewed before adoption and tracked in catalogs
- Force-push to `main` is prohibited
- CI validates all changes before merge
