# hoa-tooling

`hoa-tooling` is a shared tooling repository for all HOA projects, independent of tech stack.

It is meant to host reusable project tooling modules. Today it provides:

1. Story System tooling
2. Docker Makefile system

More tool modules will be added over time in this same repository.

## Tool Modules

### 1) Story System

Path:
- `stories/`
- `.claude/commands/`

Purpose:
- standardize user-story writing, review, implementation flow
- enforce testable acceptance criteria and validation tasks
- keep backlog structure consistent across projects

### 2) Docker Makefile System

Path:
- `hoa-docker-makefile.md`

Purpose:
- provide a stable Makefile convention for Docker projects
- keep target naming consistent (`up`, `down`, `logs`, `test`, `migrate`, ...)
- reduce project-to-project operational friction

## Install In Any Project (Submodule)

From target project root:

```bash
git submodule add git@github.com:<org-or-user>/hoa-tooling.git tooling/hoa-tooling
git submodule update --init --recursive
```

## Enable Story System In Target Project

```bash
mkdir -p stories/by-feature
cp tooling/hoa-tooling/stories/STORY-TEMPLATE.md stories/STORY-TEMPLATE.md
cp tooling/hoa-tooling/stories/README.md stories/README.md
cp tooling/hoa-tooling/stories/backlog.md stories/backlog.md
mkdir -p .claude/commands
cp tooling/hoa-tooling/.claude/commands/*.md .claude/commands/
```

Then replace example stories/backlog entries with your project-specific scope.

## Enable Docker Makefile System In Target Project

1. Open `tooling/hoa-tooling/hoa-docker-makefile.md`
2. Copy the Makefile blueprint into project root `Makefile`
3. Adapt internal commands to your stack while keeping target names stable

## Daily Usage Commands (Story Workflow)

```text
/new-story
/review-story stories/by-feature/<area>/story-XXX-<slug>.md
/implement-story stories/by-feature/<area>/story-XXX-<slug>.md
```

## Update Tooling Version In A Project

```bash
git submodule update --remote --merge tooling/hoa-tooling
```

## Repository Direction

This repository is intentionally modular.

Current modules:
- Story System
- Docker Makefile system

Planned future modules (examples):
- CI pipeline templates
- release/versioning helpers
- security checklists
- repository bootstrap scripts
