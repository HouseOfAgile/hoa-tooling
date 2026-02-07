# hoa-tooling

`hoa-tooling` is a modular repository of reusable tooling/features that can be used in any project, regardless of stack.

It is designed as a toolbox: each tool has its own directory and README.

## Tools Catalog

### `tools/story-system`

Provides:
- story template
- backlog example
- example stories
- command docs for story lifecycle (`new`, `review`, `implement`)

See: `tools/story-system/README.md`

### `tools/docker-makefile-system`

Provides:
- Docker-oriented Makefile conventions and blueprint

See: `tools/docker-makefile-system/README.md`

## Install In Any Project (Recommended: Submodule)

From target project root:

```bash
git submodule add git@github.com:<org-or-user>/hoa-tooling.git tooling/hoa-tooling
git submodule update --init --recursive
```

## Quick Enable Commands

### Enable Story System

```bash
mkdir -p stories/by-feature
cp tooling/hoa-tooling/tools/story-system/STORY-TEMPLATE.md stories/STORY-TEMPLATE.md
cp tooling/hoa-tooling/tools/story-system/backlog.example.md stories/backlog.md
mkdir -p .claude/commands
cp tooling/hoa-tooling/tools/story-system/commands/*.md .claude/commands/
```

### Enable Docker Makefile System

```bash
cp tooling/hoa-tooling/tools/docker-makefile-system/hoa-docker-makefile.md ./docs/hoa-docker-makefile.md
```

Then create/update project `Makefile` from the blueprint.

## Keep Tooling Updated

```bash
git submodule update --remote --merge tooling/hoa-tooling
```

## Future Direction

This repository will grow with additional tooling modules.

Planned categories include:
- CI/CD templates
- release/version helpers
- security checklists
- repository bootstrap scripts
