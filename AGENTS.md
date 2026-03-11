# Repository Guidelines

## Project Structure & Module Organization
This repository is currently minimal. The top level contains:

- `README.md`: the only tracked project document at the moment.
- `.git/`: repository history and configuration.

Keep new source files grouped by purpose as the project grows. Prefer a simple layout such as `src/` for implementation code, `tests/` for automated tests, and `assets/` for static files. Use clear, feature-oriented names like `src/parser.py` or `tests/test_parser.py`.

## Build, Test, and Development Commands
No build system or test runner is configured yet. Until tooling is added, use basic git and file inspection commands:

- `git status`: review working tree changes before committing.
- `git log --oneline`: inspect recent history and commit style.
- `ls -la`: verify repository contents.

If you introduce a language toolchain, document the canonical local commands in `README.md` and keep them consistent with this guide.

## Coding Style & Naming Conventions
Match the conventions of the language you add. Default expectations for this repository:

- Use 4 spaces for indentation in code and one sentence per line in Markdown where practical.
- Prefer descriptive file names and lowercase-with-separators naming such as `feature_flag.py`, `build-script.sh`, or `test_api.js`.
- Keep modules focused and avoid mixing source, generated files, and large assets in the repository root.

When you add formatting or linting tools, commit their config files with the related code.

## Testing Guidelines
Add automated tests alongside any non-trivial logic. Place them under `tests/` and mirror the source layout where possible. Use names that make intent obvious, such as `test_readme_links` or `parser.spec.ts`.

Before opening a pull request, run the project’s documented test command locally and note any gaps if no automated coverage exists yet.

## Commit & Pull Request Guidelines
Git history currently starts with `Initial commit`, so there is no established detailed convention yet. Use short, imperative commit messages such as `Add contributor guide` or `Create test scaffold`.

Pull requests should include:

- A brief summary of what changed.
- Any setup, testing, or verification performed.
- Linked issues or follow-up work, if applicable.

Include screenshots only when a change affects rendered output or documentation visuals.
