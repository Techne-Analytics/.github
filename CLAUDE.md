# CLAUDE.md — Techne Analytics .github Repo

Organization-wide GitHub defaults. Changes here propagate to all Techne-Analytics repos that don't override them.

## What this repo is

The special `.github` repository for the Techne-Analytics GitHub org. Contains default issue templates, PR templates, contributing guidelines, label definitions, and release config.

## Conventions

- **Semantic commits**: `feat:`, `fix:`, `docs:`, `chore:`
- **Branch prefixes**: `feat/`, `fix/`, `docs/`, `chore/`
- **Labels**: defined in `.github/labels.yml` — edit there, not in GitHub UI
- **Templates**: YAML-based issue forms, Markdown PR templates

## Editing guidelines

- Keep templates minimal — repos can override with their own
- Label names use `type:`, `priority:`, `status:` prefixes for consistency
- Test YAML issue forms with GitHub's template preview before merging
- Changes to labels.yml trigger the label-sync workflow on push to main
