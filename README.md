# hoa-tooling

`hoa-tooling` is a modular repository of reusable tooling/features that can be used in any project, regardless of stack.

It is designed as a toolbox: each tool has its own directory and README.

## Tooling Model

1. Add `hoa-tooling` as a submodule in any project.
2. Ask your AI agent to apply one tool by name.
3. Agent reads tool definition and bootstraps capabilities in that project.

This keeps workflows consistent while staying stack-agnostic.

## Tools Catalog

See full index: `tools/README.md`

### `story-system`

Provides:
- story template
- backlog example
- example stories
- command docs for story lifecycle (`new`, `review`, `implement`)

See: `tools/story-system/README.md`

### `hoa-docker-makefile`

Provides:
- Docker-oriented Makefile conventions and blueprint

See: `tools/docker-makefile-system/README.md`

## Install In Any Project (Recommended: Submodule)

From target project root:

```bash
git submodule add git@github.com:HouseOfAgile/hoa-tooling.git tooling/hoa-tooling
git submodule update --init --recursive
```

## Agent Activation Prompts

After adding the submodule, tell your agent one of these:

- `add the story system to this project`
- `bootstrap makefile following the tool definition hoa-docker-makefile`

You can keep this phrasing pattern for future tools:
- `apply tool <tool-name> to this project`

Manual setup commands are documented in each tool README.

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
