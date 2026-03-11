# Changelog Source Checklist

Use this checklist to turn repository changes into release notes.

## Confirm the release target

- Read `VERSION`.
- Check for release bump commits such as `chore(release): bump version to X.Y.Z`.
- Check deployment metadata if the repo stores version numbers elsewhere.

## Confirm the changelog style

- Read the top of each existing `CHANGELOG*` file.
- Reuse the existing heading order, release date format, and language structure.

## Inspect the diff in layers

1. Branch-level scope:
   `git diff --stat <base>...HEAD`
2. Commit-level summaries:
   `git log --oneline --decorate -n 20`
3. File-level confirmation:
   inspect the changed files behind the most important commits

## High-signal files

- API handlers, schemas, DTOs
- domain or application services
- migrations and init SQL
- deployment manifests and environment variable docs
- frontend routes, pages, hooks, API clients
- integration tests that demonstrate user flows
- OpenAPI or protocol specs

## Low-signal files

- formatting-only edits
- generated artifacts with no behavior change
- lockfile churn unless it unlocks a notable capability
- purely internal renames

## Mapping rules

- Many files, one capability: summarize once.
- One feature with backend + frontend + docs changes: write one bullet, not three.
- Schema changes: mention upgrade or compatibility impact.
- New API endpoint: mention endpoint only if it is useful to operators or integrators.
- Tests: mention them when they validate a significant new flow or reliability improvement.

## Multilingual changelog rule

If both English and Chinese changelogs exist:

- update both in the same change
- keep sections aligned
- keep the same factual scope
- adapt wording naturally instead of translating line-by-line
