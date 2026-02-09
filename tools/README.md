# Tools Index

`hoa-tooling` is a collection of reusable tools/features.

Each tool has:
- a stable tool name
- its own directory
- its own README with setup steps

## Available Tools

## `story-system`

Path:
- `tools/story-system/`

Use when you want:
- story/backlog workflow
- acceptance-criteria-driven implementation
- validation-task discipline

Agent prompt example:
- `add the story system to this project`

## `hoa-docker-makefile`

Path:
- `tools/docker-makefile-system/`

Use when you want:
- standardized Docker Makefile commands
- consistent `make up/down/logs/test/migrate` workflow
- environment-aware compose + dotenv resolution
- backup/restore/cache/diagnostic targets scaffolded

Agent prompt example:
- `bootstrap makefile following the tool definition hoa-docker-makefile`

## `activity-log`

Path:
- `tools/activity-log/`

Use when you want:
- standardized session tracking across AI agents
- continuity between agent sessions (what was done, what's pending)
- local-only, gitignored activity log per project

Agent prompt example:
- `set up the activity log for this project`

## Pattern For Future Tools

When adding a new tool:
1. Create `tools/<tool-name>/`
2. Add `tools/<tool-name>/README.md`
3. Document canonical agent prompt(s)
4. Add tool entry in this index
