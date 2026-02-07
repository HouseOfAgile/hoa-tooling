# hoa-tooling

Portable delivery tooling for any software project, independent of stack.

Use this repository to standardize how teams define stories, review scope, implement features, and validate outcomes.

## What You Get

- `stories/`
  - reusable story template
  - backlog format
  - example stories (for reference only)
- `.claude/commands/`
  - `/new-story`
  - `/review-story`
  - `/implement-story`
- `hoa-docker-makefile.md`
  - reusable Docker-oriented Makefile conventions

## Fastest Setup (Submodule)

From your project root:

```bash
git submodule add git@github.com:<org-or-user>/hoa-tooling.git tooling/hoa-tooling
git submodule update --init --recursive
```

## Enable The Story System In Your Project

1. Create project story folders:

```bash
mkdir -p stories/by-feature
```

2. Copy baseline files from tooling:

```bash
cp tooling/hoa-tooling/stories/STORY-TEMPLATE.md stories/STORY-TEMPLATE.md
cp tooling/hoa-tooling/stories/README.md stories/README.md
cp tooling/hoa-tooling/stories/backlog.md stories/backlog.md
```

3. Copy Claude command docs (optional but recommended):

```bash
mkdir -p .claude/commands
cp tooling/hoa-tooling/.claude/commands/*.md .claude/commands/
```

4. Adapt `stories/backlog.md` to your domain (replace example stories).

## Daily Workflow Commands

Use these commands in your AI tooling environment:

```text
/new-story
/review-story stories/by-feature/<area>/story-XXX-<slug>.md
/implement-story stories/by-feature/<area>/story-XXX-<slug>.md
```

## Keep Tooling Updated

When using submodule:

```bash
git submodule update --remote --merge tooling/hoa-tooling
```

Then review and commit updated tooling files in your project.

## Docker Makefile Standard

Use `tooling/hoa-tooling/hoa-docker-makefile.md` as the base to create a root `Makefile` with stable commands (`up`, `down`, `logs`, `test`, `migrate`) across projects.

## Notes

- The example stories in this repo are demonstrations of format and quality bar.
- Your real product backlog should live in your project repository.
- Keep `Validation Tasks` mandatory in all implementation stories.
