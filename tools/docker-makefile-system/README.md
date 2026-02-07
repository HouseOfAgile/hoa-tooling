# Docker Makefile System

Reusable Makefile conventions for Docker-managed projects.

## What This Tool Provides

- A stable command naming convention across projects
- A copy-ready Makefile blueprint
- A full tool definition/spec that agents can follow
- Guidance for adapting command internals to any stack

## Files

- `hoa-docker-makefile.md`: canonical tool definition/specification
- `Makefile.template`: implementation template aligned with the tool definition

## How To Use In Another Project

From your project root:

```bash
cp tooling/hoa-tooling/tools/docker-makefile-system/hoa-docker-makefile.md ./docs/hoa-docker-makefile.md
```

Then create/update your root `Makefile` from `Makefile.template` and adapt context values.

## Agent Prompt (Recommended)

After adding `hoa-tooling` as submodule, tell your agent:

- `bootstrap makefile following the tool definition hoa-docker-makefile`

This prompt should make the agent:

1. Read `hoa-docker-makefile.md`
2. Fill project context values
3. Generate/adjust root `Makefile` from `Makefile.template`
4. Explain assumptions and any required manual follow-up

## Recommended Stable Targets

- `make up`
- `make down`
- `make ps`
- `make logs`
- `make test`
- `make lint`
- `make migrate`

Keep target names stable; adapt command internals per stack.
