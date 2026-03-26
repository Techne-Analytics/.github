# Contributing to Techne Analytics

Thanks for contributing. This guide applies to all Techne-Analytics repositories unless a repo provides its own `CONTRIBUTING.md`.

## Quick start

1. Fork the repo (or branch from `main` if you have write access)
2. Create a branch with the appropriate prefix
3. Make your changes, commit with conventional messages
4. Open a pull request
5. Address review feedback

## Branch naming

All branches must use a prefix:

| Prefix | Use when |
|--------|----------|
| `feat/` | Adding new functionality |
| `fix/` | Fixing a bug |
| `docs/` | Documentation-only changes |
| `refactor/` | Restructuring without behavior change |
| `chore/` | Tooling, CI, dependencies, config |
| `test/` | Adding or updating tests |

Example: `feat/scaffold-p2-template`

## Commit messages

We use [Conventional Commits](https://www.conventionalcommits.org/). Every commit message must follow this format:

```
type(scope): description

[optional body]
```

**Types:** `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `ci`

**Scope** is optional but encouraged — use the area of the codebase affected (e.g., `catalog`, `framework`, `scaffold`, `eval`).

**Examples:**
```
feat(scaffold): add P2 overlay for knowledge retrieval
fix(catalog): correct MCP server security_notes field
docs: update onboarding guide with new make targets
chore(ci): add framework validation to workflow
```

**Why this matters:** PR titles are validated against this format in CI. Release notes are auto-generated from commit types.

## Pull requests

- Fill out the PR template completely — summary, test plan, notes
- Keep PRs focused on a single concern
- Run the repo's test/validation suite before requesting review
- PRs require at least one approval before merging

## Issues

Use the issue templates provided:
- **Bug** — something is broken or behaving unexpectedly
- **Feature** — proposing new functionality
- **Task** — internal work item (chores, refactors, research)

## Code style

Each repo defines its own style rules. General principles:
- Write clear, self-documenting code
- Prefer small, single-purpose functions
- Include tests for new behavior
- Don't commit secrets, credentials, or `.env` files

## Questions?

Open a discussion or reach out to the maintainers listed in the repo's README.
