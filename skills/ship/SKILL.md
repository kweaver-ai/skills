---
name: ship
description: Run regression tests, commit all changes, and push to remote. Use when the user wants to validate, commit, and ship the current work in one step.
---

# Ship

Run regression tests, commit all changes (staged + unstaged), and push to remote.

## Steps

### 1. Pre-flight Check

Run `git status` to see all modified, staged, and untracked files. If there are no changes at all, stop and inform the user.

### 2. Detect Test Runner

Inspect the project root to determine the appropriate test command:

| Signal file | Test command |
|-------------|-------------|
| `package.json` with `"test"` script | `npm test` |
| `pytest.ini` / `pyproject.toml` / `setup.py` / `setup.cfg` | `python -m pytest tests/ -v` |
| `go.mod` | `go test ./...` |
| `Cargo.toml` | `cargo test` |
| `Makefile` with `test` target | `make test` |

If no test runner is detected, skip the regression step and inform the user.

### 3. Regression

Run the detected test command. If any test fails, stop and report the failures. Do **not** proceed to commit.

### 4. Commit

Generate a commit for all current changes using the `/commit` skill. The `/commit` skill will stage and commit all changes (both staged and unstaged).

### 5. Push

After the commit is created, push the current branch to the remote:
- If the branch already has an upstream: `git push`
- If not: `git push -u origin <branch>`
