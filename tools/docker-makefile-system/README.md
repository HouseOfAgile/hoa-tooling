# Docker Makefile System

Reusable Makefile conventions for Docker-managed projects.

## What This Tool Provides

- A stable command naming convention across projects
- A copy-ready Makefile blueprint
- Guidance for adapting command internals to any stack

## Files

- `hoa-docker-makefile.md`: canonical blueprint and conventions

## How To Use In Another Project

From your project root:

```bash
cp tooling/hoa-tooling/tools/docker-makefile-system/hoa-docker-makefile.md ./docs/hoa-docker-makefile.md
```

Then create/update your root `Makefile` by following that blueprint.

## Agent Prompt (Recommended)

After adding `hoa-tooling` as submodule, tell your agent:

- `bootstrap makefile following the tool definition hoa-docker-makefile`

## Recommended Stable Targets

- `make up`
- `make down`
- `make ps`
- `make logs`
- `make test`
- `make lint`
- `make migrate`

Keep target names stable; adapt command internals per stack.
