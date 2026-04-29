# skills

This repository stores reusable Codex skills tracked in git for review and sharing.

## Layout

- `skills/`: skill definitions copied into this repository.
- `skills/<skill-name>/SKILL.md`: the main instruction file for each skill.
- `AGENTS.md`: contributor guidance for updating this repository.

## Included Skills

- `changelog-release-notes`: guidance for drafting changelogs and release notes from repository evidence.
- `create-github-pull-request-from-specification`: guidance for creating a GitHub pull request from a written specification.
- `generate-implementation-design`: guidance for turning a PRD into a Chinese implementation design document using staged clarification, a fixed template, and C4-oriented HLD/LLD structure.
- `kweaver-expr`: load / save / prune team's KWeaver operational experience library at `~/.expr/kweaver/`.

## Installing Skills for Claude Code

Claude Code only discovers skills under `~/.claude/skills/`. Symlink each skill from this repo so updates flow through `git pull`:

```sh
# one skill
ln -s "$(pwd)/skills/kweaver-expr" ~/.claude/skills/kweaver-expr

# or all skills at once
for d in skills/*/; do
  name=$(basename "$d")
  ln -sfn "$(pwd)/$d" "$HOME/.claude/skills/$name"
done
```

Restart your Claude Code session afterwards. Invoke a skill with `/<skill-name>` (e.g. `/kweaver-expr load`).

> Prefer symlinks over `cp -r` so the repo stays the single source of truth for the team.

## Updating Skills

To add or refresh a skill, copy it from your local Codex skill directory into `skills/` and commit the result. Example:

```sh
cp -R ~/.codex/skills/<skill-name> skills/
git add skills/<skill-name>
git commit -m "Add <skill-name> skill"
```

Keep each skill in its own directory and avoid mixing unrelated changes in the same commit.
