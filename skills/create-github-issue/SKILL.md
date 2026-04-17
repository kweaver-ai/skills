---
name: create-github-issue
description: Create a GitHub issue from the current conversation context, then create and switch to a linked branch. Use when the user wants to track a feature or bug as an issue and start working on it immediately.
---

# Create GitHub Issue

Create a GitHub issue based on the problem or feature discussed above, then create and switch to a linked branch.

## Input

`$ARGUMENTS` — branch type: `"feature"` or `"bugfix"` (default: `"feature"`)

## Steps

1. **Analyze the conversation** to identify the problem or feature discussed. Summarize it into:
   - A concise issue title
   - A detailed issue body (background, expected behavior, steps to reproduce if applicable)

2. **Detect submodules**: Run `basename $(git rev-parse --show-toplevel)` to get the repo name. If the current directory is inside a submodule or the issue targets a specific module, prefix the issue title with `【{module name}】`.

3. **Create the GitHub issue** using `gh issue create`:
   - Use the title and body from step 1
   - Add appropriate labels if they exist (`bug`, `enhancement`, etc.)
   - Capture the issue number from the output

4. **Create a branch** based on the argument type:
   - `feature` → `feature/{issue-number}-{short-desc}`
   - `bugfix` → `bugfix/{issue-number}-{short-desc}`
   - `{short-desc}` is a kebab-case summary (3–5 words) derived from the issue title

5. **Switch to the new branch**: `git checkout` to the newly created branch.

6. **Report** the issue URL and branch name to the user.

## Rules

- `{short-desc}` must be lowercase kebab-case, no special characters, max 5 words.
- Always confirm the issue was created successfully before creating the branch.
- If `gh` CLI is not authenticated, inform the user and stop.
