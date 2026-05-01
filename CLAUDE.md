# CLAUDE.md — Techne-Analytics organization

Shared Claude-readable rules for all Techne-Analytics repositories. Per-repo `CLAUDE.md` files document repo-specific content and link here for org-wide rules.

> **Working in this repo specifically?** This `.github` repo also holds GitHub defaults (issue templates, PR template, labels, release config, workflows). Edits here propagate via GitHub's `.github`-repo inheritance to any Techne-Analytics repo without its own override.

## Company context

- Techne Analytics — Colorado data engineering + AI consulting firm
- Team: Ben Dengerink (Founder, strategy/architecture), Clay Cousins (Partner & COO, delivery/ops), Jenn (Partnerships Lead)
- Mid-market clients ($10M-$500M revenue) across logistics, PE, accounting, healthcare, insurance
- Services: Data Engineering, Analytics & BI, Agentic AI

## Preferred stack

- **Web apps:** Next.js (latest), Tailwind CSS, shadcn/ui, dark mode default
- **Fonts:** Geist Sans (UI), Geist Mono (code/metrics)
- **AI features:** AI SDK v6 + Vercel AI Gateway (OIDC auth, not direct provider keys)
- **Deploy:** Vercel
- **Database:** Neon Postgres when needed (via Vercel Marketplace)
- **Backend Python:** SQLAlchemy 2.0 + Alembic
- **CRM:** Pipedrive
- **Project management:** Linear (team: Techne Analytics)
- **Data warehouse:** Snowflake, dbt
- **Orchestration:** Airflow / Astronomer

## Git conventions

- **Conventional Commits:** `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `ci` — must match `.github/labels.yml` and `CONTRIBUTING.md`.
- **Branch prefixes:** `feat/`, `fix/`, `docs/`, `refactor/`, `chore/`, `test/`, `ci/`.
- **Squash merge** PRs.
- **Co-author line:** `Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>`.

## PR review workflow

- After opening any PR on a Techne-Analytics repo: immediately invoke `pr-review-toolkit:review-pr` and address findings.
- Wait for Codex (and Copilot, if configured) to submit their reviews.
- Address all review feedback in subsequent commits with replies linking to fix commits.

## Testing discipline

- **Plan tests first.** When writing an implementation plan (`superpowers:writing-plans`), each step that introduces logic must list the test cases *before* the implementation. Tests are not a separate phase — they're part of the step.
- **Every function that interprets an external API response gets unit tests** covering at minimum (a) the documented success shape and (b) one documented-error shape. Mock the HTTP client at the boundary. This catches the silent-success class of bug (wrong field name, schema drift, nullable-overwrite-on-conflict) at near-zero cost.
- **"Lift-and-shift / migration" is NOT an automatic exception.** If you'd defer tests, surface the choice and ask — don't suppress test-coverage findings in the reviewer prompt.

## Vercel gotchas

- **Use the team scope** for `vercel link`. Run `vercel switch techne-analytics` first — Hobby (personal) scope can't link private org repos and silently misroutes the link.
- **Pipe secrets via stdin, never use `--value`.** The CLI echoes `--value` arguments back in error messages, leaking secrets into shell logs and conversation transcripts. Pattern: `printf '%s' "$VAL" | vercel env add KEY production`.
- **Preview env-add via CLI is broken** in non-interactive mode — demands a `<gitbranch>` arg even when help says it's optional. Use the Vercel UI for preview env vars, or skip preview for keys only the production runtime needs.

## Agent safety rules

- Always run pre-commit checks before pushing.
- Don't force-push to main.
- Don't commit `.env` or any file containing `DATABASE_URL` value.
- Don't deploy to production unless explicitly asked.

### Merge autonomy on Techne-Analytics repos

Agents may squash-merge a PR without further confirmation when ALL of:

1. CI is green on the head SHA.
2. `pr-review-toolkit:review-pr` has been run with no unaddressed blocking findings.
3. Codex (and Copilot, if configured) reviews have submitted; any P1/P2 issues are addressed in subsequent commits with replies linking to fix commits.
4. The PR is not a production deploy or release gate (cron flips, `vercel.json` schedule changes, alembic migrations on the prod branch).

If any condition is unmet, ask first. The "don't deploy to production" rule still applies separately — agent-merging a code change is fine; flipping a deploy gate is not.

## Linear conventions

- All non-trivial work gets a Linear ticket in the **Techne Analytics** team.
- Branch names match Linear's `gitBranchName` format (e.g. `feat/tec-305-…`).
- PR title or body links the ticket; merging PRs auto-transitions the linked ticket to Done.

## Claude Code GitHub Action setup (when adding `@claude` to a repo)

- Inline `.github/workflows/claude.yml` (do NOT use a reusable workflow — hits `startup_failure` when invoked from private callers referencing the org `.github` repo).
- Set `CLAUDE_CODE_OAUTH_TOKEN` as a **repo-level** secret via `gh secret set CLAUDE_CODE_OAUTH_TOKEN --repo Techne-Analytics/<repo>` (org-level secrets silently resolve to empty in private repo workflows on Free plan).
- The Claude GitHub App is already installed on the `Techne-Analytics` org — no per-repo install needed.
- Canonical org name in workflow `uses:` refs is `Techne-Analytics` (case-sensitive).

## Editing this file

- Run `claude-md-management:claude-md-improver` on every edit before pushing.
- Per-repo CLAUDE.md files should NOT duplicate sections from this file — they should link here via the header pointer documented in the spec (`docs/superpowers/specs/2026-05-01-tec-327-contributor-baseline-design.md` in techne-sales-pipeline).
- Label-sync workflow + release notes config remain in `.github/`; they don't need a section here.
